<!-- Source: https://create.roblox.com/docs/sv-se/cloud-services/extended-services -->

Utökade tjänster | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Utökade tjänster

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Utökade tjänster är en lösning som låter dig hantera tjänstanvändning och betalning utöver Robloxs standardgränser. Det inkluderar datalagring, minneslagring, text-till-tal, tal-till-text och beräkning.

## [Behörighetskrav](#behörighetskrav)[](#behörighetskrav)

För att använda utökade tjänster måste ditt Roblox-konto:

-

Vara [ID-verifierat](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  och vara 18 år eller äldre.

-

Vara beläget i ett [stödt land](#st%C3%B6dda-l%C3%A4nder) .

-

Ha en giltig e-postadress kopplad till det.

-

Inte för närvarande vara avstängd eller modererad.

-

Acceptera och följa [användarvillkoren](https://en.help.roblox.com/hc/articles/37967848292500) .

För gruppkonton behöver endast gruppens ägare uppfylla behörighetskraven.

## [Lås upp utökade tjänster](#lås-upp-utökade-tjänster)[](#lås-upp-utökade-tjänster)

Om du uppfyller alla [behörighetskrav](#beh%C3%B6righetskrav)  kan du slutföra inställningen av utökade tjänster genom att ange dina kontouppgifter och betalningsinformation. För gruppägda spel kan endast gruppens ägare låsa upp utökade tjänster och registrera spelet för det.

För att låsa upp och använda utökade tjänster:

1.

Gå till [Skapardashbordet](https://create.roblox.com/dashboard/creations) , gå till Skapelser  och välj ett spel.

2.

Gå till Utökade tjänster .

3.

Om du inte har angett dina kontouppgifter och betalningsinformation ännu, klicka på Lägg till saknad information  i den övre bannern.

1.

Ange din kontoinformation. Fälten Kontotyp , Skatte-ID-typ  och Skatte-ID  är valfria.

-

Du kan också gå till Ekonomi  ⟩ Kontoinformation  under avsnittet Utökade tjänster  för att hantera din kontoinformation. Du behöver inte uppdatera något annat på denna sida.

2.

Klicka på Nästa .

3.

Ange en betalningsmetod. Du kan ange en ny betalningsmetod eller välja från de tillgängliga betalningsalternativen som redan är kopplade till ditt Roblox-konto.

-

Du kan också gå till Ekonomi  ⟩ Betalningar  för att lägga till nya betalningsmetoder, eller gå till Ekonomi  ⟩ Fakturering  för att ställa in en ny standardbetalningsmetod.

4.

Klicka på Spara .

##### Kontostatus

Ditt konto för utökade tjänster kan vara i en av följande statusar:

| Status | | Beskrivning | | Krävd åtgärd |
| Normal | | Du kan använda alla funktioner för utökade tjänster. | | Ingen åtgärd krävs. |
| --- | --- |
| Förfallen | | Ditt konto är förfallet eftersom din automatiska betalningsmetod misslyckades. Roblox erbjuder en nådperiod på sju dagar  innan ditt konto för utökade tjänster stängs av. | | Ändra din betalningsmetod och försök med en manuell betalning, eller vänta tills Roblox försöker debitera din betalningsmetod igen efter att nådperioden har avslutats. |
| Avstängd | | Du kan inte använda några betalda utökade tjänster. Du kan dock fortfarande använda tjänster med standardgränser. | | Åtgärda dina behörighetskrav, lägg till en giltig betalningsmetod eller betala manuellt den förfallna saldot på ditt konto. |

## [Aktivera en tjänst](#aktivera-en-tjänst)[](#aktivera-en-tjänst)

För att aktivera en tjänst:

1.

Gå till Utökade tjänster .

2.

Slå på den tjänst du vill aktivera.

3.

Ange en månadsbudget för varje tillämplig resurs under tjänsten. Den minimi månadsbudget du kan ställa in är $0.50 USD.

Din betalningsmetod debiteras antingen i slutet av månaden när en faktura genereras, eller när din användning når $10 USD, vilket som kommer först.

Du kan öka eller minska en tjänsts månadsbudget när som helst. Din tjänst begränsas automatiskt om du minskar din budget till ett belopp under din nuvarande användning för månaden, eller om du överskrider den budget du har ställt in.

Roblox meddelar dig via e-post när din användning når 80% av din budget, och sedan igen när den når 100%.

### [Utökade tjänster för beräkning](#utökade-tjänster-för-beräkning)[](#utökade-tjänster-för-beräkning)

Varje spelserver får en standardmängd CPU, som växer med varje spelare som går med. Utökade tjänster för beräkning  mer än fördubblar den per-spelare CPU som dina spels servrar får.

Den stora majoriteten av spel på Roblox ser ingen fördel av denna tjänst, men spel med tung server-sidans fysik eller som gör omfattande användning av [serverauktoritet](/docs/en-us/projects/server-authority)  når befintliga gränser. För att se om ditt spel kan dra nytta av Utökade tjänster för beräkning :

-

Kontrollera [serverns hjärtslag](/docs/en-us/performance-optimization/identify#server-compute)  för bestående nedgångar under 60 FPS.

-

Granska CPU-kärnornas utnyttjande på [Prestandadashbordet](/docs/en-us/production/analytics/performance#server-charts) .

Innan du betalar för mer CPU, försök att [minska arbetsbelastningen på dina servrar](/docs/en-us/performance-optimization/improve) .

## [Hantera fakturering](#hantera-fakturering)[](#hantera-fakturering)

För att få tillgång till faktureringsdashbord för utökade tjänster:

1.

Gå till Ekonomi  ⟩ Fakturering .

2.

Välj fliken Molntjänster  för att visa följande:

-

Ditt utestående saldo, inklusive kostnad för månaden hittills

-

Din faktureringshistorik, inklusive all fakturering för utökade tjänster över dina spel

För en detaljerad sammanställning av dina aktuella utestående saldon, klicka på Visa detaljer  bredvid din betalningsmetod. För en detaljerad faktura av en tidigare faktura, klicka på Visa faktura  under Faktureringshistorik .

## [Tjänstepriser](#tjänstepriser)[](#tjänstepriser)

Se följande tabell för priser för utökade tjänster:

| Tjänst | |  | | Standard | | Utökad |
| [Minneslagring](https://create.roblox.com/docs/cloud-services/memory-stores) | | Förfrågningar | | 1000 + (CCU × 120) förfrågningar per minut | | $0.003 / 1M förfrågningar |
|  | | Lagring | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB per timme¹ |
| [Text-till-tal](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Förfrågningar | | 1 + (CCU × 6) förfrågningar per minut | | $5.00 / 1M förfrågningar |
| [Tal-till-text](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Förfrågningar | | 1 + (CCU × 5) förfrågningar per minut | | $1 / 1M förfrågningar |
| [Standard datalagring](https://create.roblox.com/docs/cloud-services/data-stores) | | Hämta | | 250 + (CCU * 40) förfrågningar per minut | | $0.08 / 1M förfrågningar |
|  | | Ställ in | | 250 + (CCU * 20) förfrågningar per minut | | $0.80 / 1M förfrågningar |
|  | | Lista | | 10 + (CCU * 2) förfrågningar per minut | | $0.60 / 1M förfrågningar |
|  | | Ta bort | | 100 + (CCU * 40) förfrågningar per minut | | $0.80 / 1M förfrågningar |
| [Ordnade datalagring ](https://create.roblox.com/docs/cloud-services/data-stores) | | Hämta | | 250 + (CCU * 40) förfrågningar per minut | | $0.08 / 1M förfrågningar |
|  | | Ställ in | | 250 + (CCU * 20) förfrågningar per minut | | $0.25 / 1M förfrågningar |
|  | | GetSorted | | 100 + (CCU * 2) förfrågningar per minut | | $0.32 / 1M förfrågningar |
|  | | Ta bort | | 100 + (CCU * 40) förfrågningar per minut | | $0.25 / 1M förfrågningar |
| [Datalagringslagring ](https://create.roblox.com/docs/cloud-services/data-stores) | | Lagring | | 100 MB + (1 MB * Livstidsspelare) GB per månad | | $0.12 / GB per månad |
| [Beräkning ](https://create.roblox.com/docs/production/analytics/performance) | | CPU-kärnor | | Första 100K spel timmar per månad utan kostnad (när registrerad i utökade tjänster för beräkning) | | $0.001 / spel timme² |

 ¹ GB per timme = lagringsförbrukningen multiplicerad med tiden. Till exempel kan 100 GB timmar motsvara "100 GB × 1 timme" eller "200 GB × 0.5 timmar".  ² Utökade tjänster för beräkning debiteras baserat på hur länge funktionen förblir aktiverad, mätt i minuter av speltid. Eftersom aktivering av funktionen reserverar ytterligare beräkningskapacitet för ditt spel, tillkommer avgifter när funktionen är aktiv, även om den extra beräkningen inte helt konsumeras. Speltimmar beräknas som summan av alla spelares sessionstider. Till exempel, om 10 000 användare spelar i 1 timme var, blir det 10 000 speltimmar, vilket resulterar i $10 i avgifter utöver den inkluderade månatliga tillåtelsen på 100 000 speltimmar. Dessa gränser och priser gäller endast för spel som är registrerade i utökade tjänster för beräkning. Spel som inte registreras fortsätter att få obegränsade speltimmar under de nuvarande standardgränserna utan extra kostnad.

## [Stödda länder](#stödda-länder)[](#stödda-länder)

Utökade tjänster är tillgängliga i följande länder:

| Land |
| Australien | | Tyskland | | Polen |
| Österrike | | Hongkong | | Portugal |
| Belgien | | Ungern | | Rumänien |
| Brasilien | | Irland | | Singapore |
| Bulgariens | | Italien | | Slovakien |
| Kanada | | Kazakhstan | | Slovenien |
| Chile | | Latvia | | Sydafrika |
| Kroatien | | Litauen | | Sydkorea |
| Cypern | | Malaysia | | Spanien |
| Tjeckien | | Malta | | Sverige |
| Danmark | | Mexiko | | Schweiz |
| Estland | | Nederländerna | | Thailand |
| Finland | | Ny Zeeland | | Storbritannien |
| Frankrike | | Norge | | USA |
| Georgien | | Peru | |  |

## [Ytterligare lokaliseringar för denna sida](#ytterligare-lokaliseringar-för-denna-sida)[](#ytterligare-lokaliseringar-för-denna-sida)

För ytterligare, lokaliserade versioner av denna sida som inte är tillgängliga i webbplatsens språkval, se följande länkar:

-

[Bulgariska (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Kroatiska (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Tjeckiska (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Danska (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Holländska (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estiska (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finska (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Grekiska (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Ungerska (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Irländska (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Lettiska (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litauiska (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Maltesiska (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugisiska - Portugal (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Rumänska (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovakiska (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Slovenska (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Svenska (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
