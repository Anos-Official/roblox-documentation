<!-- Source: https://create.roblox.com/docs/sv-se/projects/groups -->

Grupper (team) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupper (team)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

En Roblox grupp  gör det möjligt för flera skapare att arbeta på samma spel, använda samma tillgångar, dela vinster och ge erkännande till alla bidragsgivare.

Gruppägande av spel hjälper skapare att samarbeta och fungera som oberoende studior. Om en konflikt uppstår inom en grupp kan Roblox inte hjälpa till att medla eller lösa oenigheter.

## [Gruppskapande](#gruppskapande)[](#gruppskapande)

Att skapa en grupp kostar 100 Robux. Du kan hantera dess [roller och behörigheter](#roller-och-beh%C3%B6righeter)  från [Skapardashbordet](https://create.roblox.com/dashboard/creations)  eller [Gemenskaper](https://www.roblox.com/communities) .

Innan du skapar en grupp, läs noggrant igenom [reglerna och förväntningarna](/docs/en-us/projects/group-guidelines)  för gruppförvaltning.

För att skapa en ny grupp:

1.

Navigera till [Skapardashbordet](https://create.roblox.com/dashboard/creations) , expandera kontoväxlaren i det övre vänstra hörnet och klicka på plus (+) -knappen.

2.

På sidan Skapa grupp , ladda upp en bild för gruppens logotyp och ange gruppnamnet.

3.

När du är redo, klicka på Köp -knappen. När gruppen har skapats kommer du att dirigeras till gruppens profilsida där du kan ändra gruppens detaljer, inklusive att lägga till upp till tre sociala länkar.

## [Roller och behörigheter](#roller-och-behörigheter)[](#roller-och-behörigheter)

Gruppmedlemmar kan tilldelas en eller flera roller  inom en grupp, och varje roll har behörigheter  som specificerar medlemmarnas förmågor.

Rollkonfiguration är endast tillgänglig om du är gruppägare eller har behörighet att skapa, konfigurera och tilldela grupproller.

För att hantera grupprolltilldelningar programatiskt från en spelserver, använd [HttpService](/docs/en-us/reference/engine/classes/HttpService)  för att anropa de stödda Open Cloud Groups-endpointarna. För installation och exempel på kod, se [Använd med Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

Från [Skapardashbordet](https://create.roblox.com/dashboard/creations) , expandera kontoväxlaren i det övre vänstra hörnet och välj gruppen.

2.

Expandera kontoväxlaren igen och välj Roller .

3.

För varje roll, bekräfta noggrant behörigheterna under Permissions -fliken.

Behörigheterna är organiserade i kategorierna General , Creation  och Community . Avsnitten nedan beskriver de behörigheter som finns tillgängliga i varje kategori.

### [Allmänt](#allmänt)[](#allmänt)

Allmänna behörigheter

| Manage roles | | Medlemmar med denna behörighet kan skapa, redigera, ta bort, omordna och tilldela eller avdela roller under sin högsta roll. De kan endast redigera behörigheter som de redan har. |
| --- | --- |
| Assign or remove roles from members | | Medlemmar med denna behörighet kan tilldela eller avdela roller under sin högsta roll till vilken medlem som helst. |
| Invite or approve members | | Medlemmar med denna behörighet kan bjuda in personer till gruppen och godkänna join-förfrågningar. |
| Kick members | | Medlemmar med denna behörighet kan ta bort medlemmar vars högsta roll är under deras egen. |
| Ban members | | Medlemmar med denna behörighet kan banna medlemmar vars högsta roll är under deras egen. |
| Configure group profile | | Medlemmar med denna behörighet kan konfigurera gruppprofilen. |
| View audit logs | | Medlemmar med denna behörighet kan se [gruppens revisionsloggar](#gruppens-revisionsloggar) . |
| Manage allies and enemies | | Medlemmar med denna behörighet kan hantera gruppens allierade och fiender. |

### [Skapande](#skapande)[](#skapande)

Creations

| Playtest experiences | | Medlemmar med denna roll kan spela alla spel som ägs av gruppen, även om de inte är släppta till en bredare publik. Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Medlemmar med denna roll kan redigera alla spel och [tillgångar](/docs/en-us/projects/assets)  som ägs av gruppen och använda alla funktioner i [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Inkluderar inte redigering av ett spel utanför en [samarbets](/docs/en-us/projects/collaboration)  session eller spara en plats från ett spel till ett annat spel. Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Medlemmar med denna roll kan både redigera spel, som ovan, och också publicera spel till Roblox. Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |
| Manage share links | | Medlemmar med denna roll kan skapa/configurera [delningslänkar](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Medlemmar med denna roll kan skapa/configurera [upplevelseevenemang](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Medlemmar med denna roll kan se alla in-game chattmeddelanden (endast läsning; medlem måste vara 18+) och banna eller hantera bannade användare över alla spel som ägs av gruppen. |
| Manage monetization for experiences | | Medlemmar med denna roll kan hantera monetiseringsprodukter som [pass](/docs/en-us/production/monetization/passes) , [utvecklarprodukter](/docs/en-us/production/monetization/developer-products) , [prenumerationer](/docs/en-us/production/monetization/subscriptions)  och mer. Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Medlemmar med denna roll kan se listan över [hemligheter](/docs/en-us/cloud-services/secrets)  och kan skapa, uppdatera och ta bort hemligheter för alla spel som ägs av gruppen. Medlemmar med denna roll kräver Edit experiences -behörighet för att se sidan Hemligheter. Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Medlemmar med denna roll kan få tillgång till [analys](/docs/en-us/production/analytics)  av alla spel som ägs av gruppen, även om de inte har redigeringsåtkomst. Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Medlemmar med denna roll kan skapa och hantera analysvarningar. Koppla denna behörighet med View analytics for experiences  för att se varningsanteckningar direkt på mätgrafiker. |

Monetization

| View group revenue | | Medlemmar med denna roll kan se gruppens Robux-balans, eventuella konfigurerade återkommande splitutbetalningar och intäktsloggningsfunktioner. |
| Manage and spend group revenue | | Medlemmar med denna roll kan se alla gruppintäkter, som ovan, och också hantera dem direkt. Detta inkluderar att ställa in [återkommande utbetalningar](#%C3%A5terkommande-utbetalningar)  och skicka [engångsutbetalningar](#eng%C3%A5ngsutbetalningar)  till samarbetspartners. |
| Create ad campaigns for the group | | Medlemmar med denna roll kan annonsera gruppen. |

Avatar items

| Create avatar items | | Medlemmar med denna roll kan skapa avatarartiklar som kläder. |
| Configure avatar items | | Medlemmar med denna roll kan konfigurera försäljningsdetaljer, påfyllningar och sponsring för befintliga gruppavatarartiklar. |

API

| Manage API keys | | Medlemmar med denna roll kan hantera [Open Cloud API-nycklar](/docs/en-us/cloud/auth/api-keys)  för gruppen. |

Development items

| View development items | | Medlemmar med denna roll kan se utvecklingsartiklar som ägs av gruppen, till exempel Ljud . |
| Manage development items | | Medlemmar med denna roll kan ladda upp och konfigurera tillgångsutvecklingsartiklar som Dekaler . |
| Manage development item permissions | | Medlemmar med denna roll kan konfigurera behörigheter för utvecklingsartiklar, till exempel ljuddelning. |

Data Stores

| View Data Stores for experiences | | Medlemmar med denna roll kan se datalager för alla gruppspel genom [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) , men de kan inte ta bort data. Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Medlemmar med denna roll kan ta bort specifika nycklar inom datalager för alla gruppspel genom [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Medlemmar med denna roll kan ta bort hela datalager för alla gruppspel genom [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Tillgänglig som en [per-spel behörighet](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Medlemmar med denna roll kan lista, skapa, uppdatera och ta bort webhooks för alla gruppupplevelser. |

Communication

| Manage support tickets for experiences | | Medlemmar med denna roll kan hantera supportärenden för alla gruppupplevelser. |

Legacy

| Hantera åtkomst till denna grupps resurser | | Medlemmar med denna roll kan skapa och redigera åtkomst till gruppens resurser. |

### [Gemenskap](#gemenskap)[](#gemenskap)

Posts

| View community announcements | | Medlemmar med denna roll kan se gemenskapsannonser. |
| Create community announcements | | Medlemmar med denna roll kan skapa gemenskapsannonser. |

Forums

| Manage categories | | Medlemmar med denna roll kan hantera forumkategorier. |
| Create posts | | Medlemmar med denna roll kan skapa foruminlägg. |
| Remove posts | | Medlemmar med denna roll kan ta bort foruminlägg. |
| Lock posts | | Medlemmar med denna roll kan låsa foruminlägg. |
| Pin posts | | Medlemmar med denna roll kan fästa foruminlägg. |
| Create comments | | Medlemmar med denna roll kan skapa kommentarer på foruminlägg. |
| Remove comments | | Medlemmar med denna roll kan ta bort kommentarer från foruminlägg. |

Content moderation

| View content moderation | | Medlemmar med denna roll kan se innehållsmoderering. |
| Manage content moderation | | Medlemmar med denna roll kan hantera innehållsmoderering. |

Miscellaneous

| Bypass slow mode | | Medlemmar med denna roll kan kringgå långsam läge. |
| View community analytics | | Medlemmar med denna roll kan se gemenskapsanalys. |

4.

VIKTIGT

 Klicka på Save -knappen för att tillämpa behörighetsinställningarna.

5.

VALFRITT

 Klicka på Settings -fliken och välj en färg och synlighetsinställning för rollen, klicka sedan på Save -knappen.

En rolls Settings -avsnitt är också där gruppägare och medlemmar med tillräckliga behörigheter kan ta bort en roll helt genom Ta bort roll -knappen.

Roller listas i hierarkisk ordning: en roll högre upp på listan har mer auktoritet än en roll nedanför. Denna ordning är viktig eftersom vissa behörigheter endast låter medlemmar hantera roller under sin egen högsta roll.

Varje roll är antingen offentlig  eller privat . Offentliga roller kan visas på en Gemenskapsida och i upplevelser. Privata roller visas endast på roll- och behörighetsförvaltningsytor för auktoriserade medlemmar, eller för medlemmar som har den privata rollen. Synlighet ändrar var en roll visas; det ändrar inte de behörigheter som rollen ger.

För att ge Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  eller Delete Data Stores for experiences  måste du ha tvåstegsverifiering aktiverad.

## [Hantera medlemmar](#hantera-medlemmar)[](#hantera-medlemmar)

Medlemskonfiguration är endast tillgänglig om du är gruppägare eller har behörighet att hantera andra medlemmar och deras roller.

För att hantera medlemmar från Skapardashbordet:

1.

Expandera kontoväxlaren i det övre vänstra hörnet och välj gruppen.

2.

Expandera kontoväxlaren igen och välj Members .

3.

Använd Medlem -fliken för att söka efter befintliga medlemmar eller filtrera dem efter roll. Använd Bjudna -fliken för att granska väntande inbjudningar.

För att lägga till en medlem, klicka på Invite -knappen och sök efter deras användarnamn. Roblox meddelar inbjudna skapare enligt deras meddelandeinställningar. Du kan också kopiera gruppens länk och dela den direkt.

### [Hantera roller](#hantera-roller)[](#hantera-roller)

Du kan hantera rolltilldelningar från antingen Members -sidan eller en specifik roll:

-

På Members -sidan, klicka på plus (+) -knappen bredvid en medlem för att öppna rollmenyn. För att tilldela en roll, klicka på plus (+) -knappen bredvid den under Lägg till roller . För att avdela en roll, klicka på minus (-) -knappen bredvid den under Nuvarande roller , eller klicka på × -knappen på en tilldelad roll bredvid medlemmens namn.

-

På Roller -sidan, välj en roll och öppna dess Members -flik. Klicka på Add members -knappen för att söka efter gruppmedlemmar och tilldela dem till rollen. För att avdela en medlem, klicka på minus (-) -knappen i slutet av deras rad.

### [Medlemsborttagning](#medlemsborttagning)[](#medlemsborttagning)

För att ta bort en medlem från gruppen, klicka på ⋮ -knappen i slutet av deras rad, välj Kicka användare , och bekräfta åtgärden.

## [Hantera utbetalningar](#hantera-utbetalningar)[](#hantera-utbetalningar)

Om du är gruppägare eller har rätt [behörighet](#roller-och-beh%C3%B6righeter)  inom Gruppintäkter , hittar du en Utbetalningar -sida under Finanser  i den vänstra navigeringen. Här kan du skicka engångsutbetalningar, samt definiera procentandelar med andra medlemmar.

Vissa grupper kanske inte har denna sida upplåst initialt av olika skäl, såsom gruppens ålder eller otillräckliga medel för utbetalning.

Utbetalningar kan inte delas mellan gruppmedlemmar för spel som tar betalt för [betald åtkomst i lokal valuta](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Engångsutbetalningar](#engångsutbetalningar)[](#engångsutbetalningar)

Engångsutbetalningar kan göras till medlemmar i en batch, där en viss summa väljs för varje. Säkerhetsfunktioner inkluderar 2FA-utmaningar, bekräftelsedialoger och kontroller kring berättigandet för medlemmar som får betalt.

 ![Engångsutbetalningsknappen som indikeras i utbetalningssektionen på Skapardashbordet.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

När du klickar på Skicka Robux -knappen kan du välja utbetalningsmottagare från popup-fönstret eller ladda upp en .csv -fil med kolumnerna userId  och payoutInRobux , till exempel:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Återkommande utbetalningar](#återkommande-utbetalningar)[](#återkommande-utbetalningar)

Återkommande utbetalningar kan också göras över hela gruppen och  per spel, där en procentandel av utbetalningen tilldelas varje medlem innan resten går in i gruppens totala balans.

 ![Splitutbetalningsknappar som indikeras i utbetalningssektionen på Skapardashbordet.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Överväg följande scenario där ett gruppspel Laser Maze  delas 40%–30%–10% mellan tre medlemmar, med en rest på 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Anta att spelet tjänar 1000 Robux, så får de tre medlemmarna 400, 300 och 100 Robux respektive (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

De återstående 200 Robux (20% av spelets split) går vidare till gruppsplit -procentandelarna, definierade som 20%–20%–10% mellan de tre medlemmarna; de får ytterligare 40, 40 och 20 Robux respektive.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

De återstående 100 Robux (50% av gruppsplit) placeras i gruppens totala balans.

 ![Exempel på flödesschema för hur spelsplitter distribueras till gruppmedlemmar först, med resten som beaktas i gruppsplit för slutlig distribution bland gruppen.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Observera att intäkter från [privata servrar](/docs/en-us/production/monetization/private-servers)  prenumerationer inte ändras om du justerar splitprocentandelar vid ett senare tillfälle, vilket innebär att om en spelare köper en privat serverprenumeration, kommer splitprocentandelarna vid tidpunkten för köpet att gälla för den specifika prenumerationen för alltid (tills den avbryts). Denna policy kan ändras i framtiden.

## [Gruppens revisionsloggar](#gruppens-revisionsloggar)[](#gruppens-revisionsloggar)

Gruppmedlemmar med View audit logs -behörighet kan granska gruppändringar med hjälp av dessa ytor för gruppförvaltning:

-

På Skapardashbordet, välj Aktivitetshistorik  under Samarbete .

-

På Gemenskaper, öppna gemenskapens konfigurationssida och välj Revisionslogg .

Gruppägare kan använda dessa loggar för att övervaka aktivitet som kan bryta mot [gruppens riktlinjer](/docs/en-us/projects/group-guidelines) .

## [Skydd av immateriella rättigheter](#skydd-av-immateriella-rättigheter)[](#skydd-av-immateriella-rättigheter)

Gruppmedlemmar med behörighet att redigera alla gruppspel kan aktivera inställningen [Platskopiering](/docs/en-us/projects/configure-games#allow-copying)  för en skapelse, vilket potentiellt tillåter hela Roblox-gemenskapen att kopiera den och använda tillgångar inom den. För att hjälpa till att skydda immateriella rättigheter i en grupp bör ägaren eller medlemmar med tillräckliga behörigheter:

-

Bekräfta att varje medlem är [tilldelad rätt roll](#hantera-roller) .

-

Kontrollera att varje grupproll har rätt [behörigheter](#roller-och-beh%C3%B6righeter) .

-

Bekräfta att inställningen [Platskopiering](/docs/en-us/projects/configure-games#allow-copying)  är inaktiverad innan privata tillgångar läggs till.

## [Ytterligare lokaliseringar för denna sida](#ytterligare-lokaliseringar-för-denna-sida)[](#ytterligare-lokaliseringar-för-denna-sida)

För ytterligare, lokaliserade versioner av denna sida som inte är tillgängliga i webbplatsens språkval, se följande länkar:

-

[Bulgariska (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Kroatiska (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Tjeckiska (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Danska (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Holländska (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estiska (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finska (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Grekiska (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Ungerska (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irländska (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Lettiska (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Litauiska (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltesiska (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugisiska - Portugal (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Rumänska (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovakiska (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovenska (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Svenska (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
