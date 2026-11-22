<!-- Source: https://create.roblox.com/docs/et-ee/cloud-services/extended-services -->

Laiendatud teenused | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Laiendatud teenused

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Laiendatud teenused on lahendus, mis võimaldab teil hallata teenuse kasutamist ja maksmist, ületades Roblox'i vaikimisi piirangud. See hõlmab andmehoidlaid, mäluhoidlaid, tekstist kõneks, kõnest tekstiks ja arvutust.

## [Sobivuse nõuded](#sobivuse-nõuded)[](#sobivuse-nõuded)

Laiendatud teenuste kasutamiseks peab teie Roblox'i konto olema:

-

[ID-kontrollitud](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  ja vähemalt 18-aastane.

-

Asuma [toetatud riigis](#toetatud-riigid) .

-

Omama kehtivat e-posti aadressi.

-

Mitte olema praegu keelatud või modereeritud.

-

Nõustuma ja järgima [teenuse tingimusi](https://en.help.roblox.com/hc/articles/37967848292500) .

Gruppide kontode puhul peab sobivuse nõudeid täitma ainult grupi omanik.

## [Laiendatud teenuste avamine](#laiendatud-teenuste-avamine)[](#laiendatud-teenuste-avamine)

Kui täidate kõik [sobivuse nõuded](#sobivuse-n%C3%B5uded) , saate laiendatud teenuste seadistamise lõpetada, sisestades oma konto andmed ja makseinfo. Gruppide omanduses olevate mängude puhul saab laiendatud teenuseid avada ja mängu sellele registreerida ainult grupi omanik.

Laiendatud teenuste avamiseks ja kasutamiseks:

1.

Minge [Looja armatuurlauale](https://create.roblox.com/dashboard/creations) , minge Loomingud  ja valige mäng.

2.

Minge Laiendatud teenused .

3.

Kui te pole veel oma konto andmeid ja makseinfot sisestanud, klõpsake ülemisel ribal Lisa puuduvad andmed .

1.

Sisestage oma konto teave. Konto tüüp , Maksu ID tüüp  ja Maksu ID  väljad on valikulised.

-

Samuti saate minna Finantsid  ⟩ Konto teave  jaotises Laiendatud teenused , et hallata oma konto teavet. Te ei pea sellel lehel midagi muud uuendama.

2.

Klõpsake Järgmine .

3.

Sisestage makseviis. Saate sisestada uue makseviisi või valida oma Roblox'i kontoga juba seotud maksevalikute hulgast.

-

Samuti saate minna Finantsid  ⟩ Maksed , et lisada uusi makseviise, või minna Finantsid  ⟩ Arveldamine , et seada uus vaikimisi makseviis.

4.

Klõpsake Salvesta .

##### Konto staatus

Teie laiendatud teenuste konto võib olla ühes järgmistest staatustest:

| Staatus | | Kirjeldus | | Nõutav tegevus |
| Normaalne | | Saate kasutada kõiki laiendatud teenuste funktsioone. | | Tegevust ei ole vaja. |
| --- | --- |
| Makse hilinenud | | Teie konto on hilinenud, kuna teie automaatne makseviis ebaõnnestus. Roblox pakub seitsme päeva  armuaega enne, kui teie laiendatud teenuste konto peatatakse. | | Muuda oma makseviisi ja proovi käsitsi makset uuesti, või oota, kuni Roblox proovib teie makseviisi uuesti laadida pärast armuaega. |
| Peatatud | | Te ei saa kasutada ühtegi tasulist laiendatud teenust. Saate siiski kasutada teenuseid, millel on vaikimisi piirangud. | | Parandage oma sobivuse nõuded, lisage kehtiv makseviis või makske käsitsi oma konto hilinenud saldo. |

## [Teenuse lubamine](#teenuse-lubamine)[](#teenuse-lubamine)

Teenuse lubamiseks:

1.

Minge Laiendatud teenused .

2.

Lülitage sisse teenus, mille soovite lubada.

3.

Sisestage igakuine eelarve iga rakendatava ressursi jaoks teenuse all. Minimaalne igakuine eelarve, mille saate seada, on 0,50 USD.

Teie makseviisi koormatakse kas kuu lõpus, kui arve genereeritakse, või kui teie kasutus ulatub 10 USD, olenevalt sellest, kumb juhtub esimesena.

Saate teenuse igakuist eelarvet igal ajal suurendada või vähendada. Teie teenus piiratakse automaatselt, kui vähendate oma eelarvet alla teie jooksva kuu kasutuse, või kui ületate seatud eelarvet.

Roblox teavitab teid e-posti teel, kui teie kasutus ulatub 80% teie eelarvest, ja seejärel uuesti, kui see ulatub 100%-ni.

### [Laiendatud teenused arvutamiseks](#laiendatud-teenused-arvutamiseks)[](#laiendatud-teenused-arvutamiseks)

Iga mängu server saab vaikimisi koguse CPU-d, mis kasvab koos iga mängijaga, kes liitub. Laiendatud teenused arvutamiseks  kahekordistavad rohkem kui mängija kohta saadud CPU.

Enamik mänge Roblox'is ei saa sellest teenusest kasu, kuid mängud, millel on rasked serveripoolse füüsika või mis kasutavad ulatuslikult [serveri autoriteeti](/docs/en-us/projects/server-authority) , saavutavad olemasolevad piirangud. Et näha, kas teie mäng saab kasu Laiendatud teenustest arvutamiseks :

-

Kontrollige [serveri südamepekslemist](/docs/en-us/performance-optimization/identify#server-compute)  püsivate languste korral alla 60 FPS.

-

Uurige CPU tuuma kasutust [Tulemuste armatuurlaual](/docs/en-us/production/analytics/performance#server-charts) .

Enne, kui maksate rohkem CPU eest, proovige [vähendada oma serverite tööd](/docs/en-us/performance-optimization/improve) .

## [Arveldamise haldamine](#arveldamise-haldamine)[](#arveldamise-haldamine)

Laiendatud teenuste arveldamise armatuurlauale pääsemiseks:

1.

Minge Finantsid  ⟩ Arveldamine .

2.

Valige Pilveteenused  vahekaart, et kuvada järgmist:

-

Teie ootel saldo, sealhulgas kuu kuni kuupäeva kulu

-

Teie arveldamise ajalugu, sealhulgas kogu laiendatud teenuste arveldamise tegevus teie mängudes

Oma praeguste ootel saldo kulude üksikasjaliku ülevaate saamiseks klõpsake oma makseviisi kõrval Vaata üksikasju . Eelmise arve üksikasjaliku arve saamiseks klõpsake Vaata arvet  jaotises Arveldamise ajalugu .

## [Teenuse hinnakujundus](#teenuse-hinnakujundus)[](#teenuse-hinnakujundus)

Vaadake järgmises tabelis laiendatud teenuste hinnakujundust:

| Teenuse | |  | | Vaikimisi | | Laiendatud |
| [Mäluhoidlad](https://create.roblox.com/docs/cloud-services/memory-stores) | | Taotlused | | 1000 + (CCU × 120) taotlust minutis | | $0.003 / 1M taotlust |
|  | | Salvestus | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB tunnis¹ |
| [Tekstist kõneks](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Taotlused | | 1 + (CCU × 6) taotlust minutis | | $5.00 / 1M taotlust |
| [Kõnest tekstiks](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Taotlused | | 1 + (CCU × 5) taotlust minutis | | $1 / 1M taotlust |
| [Standardsed andmehoidlad](https://create.roblox.com/docs/cloud-services/data-stores) | | Saada | | 250 + (CCU * 40) taotlust minutis | | $0.08 / 1M taotlust |
|  | | Seada | | 250 + (CCU * 20) taotlust minutis | | $0.80 / 1M taotlust |
|  | | Loetle | | 10 + (CCU * 2) taotlust minutis | | $0.60 / 1M taotlust |
|  | | Eemalda | | 100 + (CCU * 40) taotlust minutis | | $0.80 / 1M taotlust |
| [Korrastatud andmehoidlad ](https://create.roblox.com/docs/cloud-services/data-stores) | | Saada | | 250 + (CCU * 40) taotlust minutis | | $0.08 / 1M taotlust |
|  | | Seada | | 250 + (CCU * 20) taotlust minutis | | $0.25 / 1M taotlust |
|  | | GetSorted | | 100 + (CCU * 2) taotlust minutis | | $0.32 / 1M taotlust |
|  | | Eemalda | | 100 + (CCU * 40) taotlust minutis | | $0.25 / 1M taotlust |
| [Andmehoidla salvestus ](https://create.roblox.com/docs/cloud-services/data-stores) | | Salvestus | | 100 MB + (1 MB * Eluaegsed mängijad) GB kuus | | $0.12 / GB kuus |
| [Arvutus ](https://create.roblox.com/docs/production/analytics/performance) | | CPU tuumad | | Esimene 100K mänguaega kuus tasuta (kui olete registreeritud laiendatud teenuste arvutamiseks) | | $0.001 / mänguaeg tund² |

 ¹ GB tunnis = salvestusmahu tarbimine korrutatud ajaga. Näiteks 100 GB tundi võib tähendada "100 GB × 1 tund" või "200 GB × 0.5 tundi".  ² Laiendatud teenused arvutamiseks arvestatakse selle põhjal, kui kaua funktsioon on lubatud, mõõdetuna mänguaegade minutites. Kuna funktsiooni lubamine reserveerib teie mängule täiendava arvutusvõime, kehtivad tasud, kui funktsioon on aktiivne, isegi kui täiendavat arvutust ei tarbita täielikult. Mänguaegade tunnid arvutatakse kõigi mängijate seansside kestuse summana. Näiteks, kui 10,000 kasutajat mängivad igaüks 1 tunni, on see 10,000 mänguaega tundi, mis toob kaasa 10 dollari tasud, mis ületavad kaasatud igakuise lubatud 100,000 mänguaega tundi. Need piirangud ja hinnakujundus kehtivad ainult mängudele, mis on registreeritud laiendatud teenuste arvutamiseks. Mängud, mis ei registreeru, jätkavad piiramatu mänguaega saamist praeguste vaikimisi piirangute alusel ilma lisatasudeta.

## [Toetatud riigid](#toetatud-riigid)[](#toetatud-riigid)

Laiendatud teenused on saadaval järgmistes riikides:

| Riik |
| Austraalia | | Saksamaa | | Poola |
| Austraalia | | Hongkong | | Portugali |
| Belgia | | Ungari | | Rumeenia |
| Brasiilia | | Iirimaa | | Singapur |
| Bulgaaria | | Itaalia | | Slovakkia |
| Kanada | | Kazahstan | | Sloveenia |
| Tšiili | | Leedu | | Lõuna-Aafrika |
| Kroatia | | Malaisia | | Lõuna-Korea |
| Küpros | | Malta | | Hispaania |
| Tšehhi | | Malta | | Rootsi |
| Taani | | Mehhiko | | Šveits |
| Eesti | | Madalmaad | | Tai |
| Soome | | Uus-Meremaa | | Ühendkuningriik |
| Prantsusmaa | | Norra | | Ameerika Ühendriigid |
| Gruusia | | Peruu | |  |

## [Täiendavad lokaliseerimised sellel lehel](#täiendavad-lokaliseerimised-sellel-lehel)[](#täiendavad-lokaliseerimised-sellel-lehel)

Täiendavate lokaliseeritud versioonide jaoks, mis ei ole saadaval saidi keelevalijas, vaadake järgmisi linke:

-

[Bulgaaria (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Kroatia (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Tšehhi (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Taani (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Hollandi (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Eesti (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Soome (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Kreeka (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Ungari (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Iiri (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Läti (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Leedu (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Malta (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugali - Portugal (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Rumeenia (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovaki (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Sloveenia (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Rootsi (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
