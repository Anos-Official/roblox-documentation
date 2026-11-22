<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/advertising -->

Adverteren met de Ads API | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Adverteren met de Ads API

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Advertising API stelt je in staat om programmatic advertenties op Roblox te creëren en te beheren. Het dekt twee soorten advertenties:

-

Ervaring advertenties  — gesponsorde campagnes die spelers naar je ervaringen brengen, via de Ads API.

Deze gids toont de gebruikelijke Ads API-stromen van begin tot eind, en de details die gemakkelijk over het hoofd worden gezien. Voor elk veld, parameter en responscode, zie de [Advertising API referentie](/docs/nl-nl/cloud/reference/features/advertising) .

De Ads API gebruikt bestaande afbeeldingsactiva. Het genereert geen AI-afbeeldingen of hernoemt creatieve activa. Voor die verzoeken, leg de beperking uit en vraag de gebruiker om de afbeelding buiten de Ads API voor te bereiden. Het uploaden van afbeeldingen is een aparte Assets API-stroom.

## [Voordat je begint](#voordat-je-begint)[](#voordat-je-begint)

Alle Ads API-eindpunten worden bediend vanaf https://apis.roblox.com/ads-management/v1 . [Genereer een API-sleutel](/docs/nl-nl/cloud/auth/api-keys) en stuur deze in de x-api-key` header van elk verzoek. Een API-sleutel of een OAuth-token fungeert als de gebruiker. Scopes beperken welke bewerkingen een applicatie kan aanroepen, en de API controleert ook de account-, groeps- en ervaringstoestemmingen van die gebruiker.

Geef de sleutel de scopes voor de stromen die je gebruikt:

| Scope | | Operaties |
| --- | --- |
| ad.campaign:read | | advertisable-universes , campaign-options , lijst en krijg campagnes, campaigns:batchGetStatus , lijst en krijg advertenties, lijst en krijg creatieven, performance-estimates , campaign-recommendations , audience-estimates |
| ad.campaign:write | | Maak en update campagnes, campaigns:validate , update advertenties, voeg creatieven toe en update deze |
| ad.billing:read | | Lijst en krijg factureringsaccounts, payment-activities , ad-credit-conversions:preview |
| universe:read | | Lees ervaring namen en eigenaren van de [Universe API](/docs/nl-nl/cloud/reference/features/universes) |
| asset:read , asset:write | | Upload creatieve afbeeldingen via de [Assets API](/docs/nl-nl/cloud/guides/usage-assets) |

De campaigns:validate  dry run heeft ad.campaign:write  nodig, maar verandert niets.

Onboarding, betaalmethoden en aankopen van advertentietegoeden zijn alleen beschikbaar in Ads Manager. De API leest het resultaat van die setup, maar kan de setup niet uitvoeren.

## [Belangrijke concepten](#belangrijke-concepten)[](#belangrijke-concepten)

-

Factureringsaccounts.  Een factureringsaccount bezit en betaalt voor campagnes. Elke gebruiker die adverteert heeft een persoonlijk account. Een groep die adverteert heeft zijn eigen account. Op lijst-eindpunten en op creatieven verzoeken (POST /creatives , GET /creatives/{id} , en PATCH /creatives/{id} ), selecteert de groupId  queryparameter het account van de groep. Zonder groupId  gebruikt het verzoek je persoonlijke account.

-

Status en leveringsstatus.  status  is de levenscyclusstatus die je beheert: ACTIEF , PAUSED , of CANCELLED , wat permanent is. deliveryStatus  is alleen-lezen en vertelt je of de campagne actief is. Zie [Volg beoordeling en levering](#volg-beoordeling-en-levering) .

-

Campagnes, advertenties en creatieven.  Een creatieve is een Roblox afbeeldingsactief dat is geregistreerd in een factureringsaccount. Een campagne adverteert één ervaring met één of meer creatieven. De campagne heeft één advertentie voor elke creatieve, en je kunt elke advertentie afzonderlijk pauzeren.

-

Doelstellingen.  Een campagne heeft één doelstelling: PLAYS , ENGAGEMENT , of ROBUX_SPEND . Niet elke doelstelling is beschikbaar voor elke ervaring, en ENGAGEMENT  accepteert geen targeting. Lees altijd de doelstellingen die campaign-options  retourneert voor de ervaring.

-

IDs en geld.  Campagne- en factureringsaccount-ID's zijn UUID's. Roblox-ID's (ervaring, actief, en groeps-ID's) en geldbedragen zijn decimale strings. Geld is in micro-USD, in velden die eindigen op Micros : "5000000"  is $5,00. Prestatie schatting velden eindigen in MicroUsd  in plaats daarvan. Stuur bedragen en ID's als JSON-strings. Een JSON-getal retourneert 400 .

-

Tijden.  Tijden zijn RFC 3339 UTC-strings. Budgetdagen en campagne-eindtijden gebruiken de tijdzone van het factureringsaccount, in timeZone .

-

Vooruitkompatibiliteit.  Antwoorden kunnen nieuwe velden en nieuwe enum-waarden krijgen. Negeer de waarden die je client niet kent.

## [Plan een campagne](#plan-een-campagne)[](#plan-een-campagne)

### [Vind een ervaring om te adverteren](#vind-een-ervaring-om-te-adverteren)[](#vind-een-ervaring-om-te-adverteren)

1.

Stuur een verzoek naar advertisable-universes  om de ervaringen te lijst die je kunt adverteren. Voeg groupId  toe om alleen de ervaringen te lijst die een groep bezit.

2.

Voor elke universum-ID, krijg de naam van GET /cloud/v2/universes/{universeId}  in de [Universe API](/docs/nl-nl/cloud/reference/features/universes) . Hetzelfde antwoord toont of een gebruiker of een groep de ervaring bezit. Als een groep het bezit, kan de campagne het factureringsaccount van de groep gebruiken.

Lijst adverteerbare ervaringen

```

curl --location 'https://apis.roblox.com/ads-management/v1/advertisable-universes' \

--header 'x-api-key: ${ApiKey}'

```

advertisable-universes  retourneert alleen ID's, in één antwoord zonder paginering.

### [Krijg de campagne-opties](#krijg-de-campagne-opties)[](#krijg-de-campagne-opties)

Roep campaign-options  aan met universeId  voordat je een campagne maakt. Het antwoord vertelt je wat een campagne voor die ervaring kan gebruiken.

Krijg campagne-opties voor een ervaring

```

curl --location 'https://apis.roblox.com/ads-management/v1/campaign-options?universeId=${UniverseId}' \

--header 'x-api-key: ${ApiKey}'

```

Lees deze velden:

| Veld | | Wat te doen met het |
| eligibility | | Als eligible  false  is, kun je de ervaring nu niet adverteren. reasons  is NO_PERMISSION  of BLOCKED , en details  heeft de oplossing. |
| objectiveOptions | | Gebruik alleen een doelstelling met available: true . unavailableReasons  legt de anderen uit. supportsTargeting  en audienceTypes  vertellen je welke targeting de doelstelling accepteert. |
| billingAccounts | | De accounts die voor deze ervaring's campagne kunnen betalen, elk met zijn paymentTypes . Geef er een door als billingAccountId  wanneer je de campagne maakt. |
| paymentTypes | | De betaalmethoden die ten minste één van de billingAccounts  kan gebruiken. Een lege lijst betekent dat geen account momenteel voor een campagne kan betalen. |
| budgetConstraints | | Het minimale budget voor elk budgettype, en de langste planning. Voor LIFETIME  is het minimum per dag van de planning. |
| creativeRequirements , adFormats , targetingDimensions | | Het aantal creatieven en actief types, de aanbevolen afbeeldingsgroottes in pixels, en de waarden die je kunt gebruiken in targeting . |
| video | | De geaccepteerde video.source  waarden, en previewVideo  voor de ervaring. Dit veld is afwezig wanneer gesponsorde video niet beschikbaar is. Zie [Voeg een video toe](#voeg-een-video-toe) . |
| mutableFields | | De campagnevelden die je later kunt wijzigen met PATCH . |

Belangrijk:  Kies zelf geen doelstelling of betaaltype. Gebruik er een die campaign-options  retourneert voor de ervaring. Als een gebruiker niet zegt welke doelstelling of betaaltype te gebruiken, toon ze de beschikbare waarden en laat ze kiezen. Als er maar één waarde beschikbaar is, gebruik deze.

Als je geen toestemming hebt om de ervaring te adverteren, retourneert campaign-options  403  met reden UNIVERSE_NOT_ADVERTISABLE . Leg de ontbrekende toestemming uit en stop met het plannen van een campagne voor die ervaring. Het aanroepen van campaign-options  zonder universeId  stelt geen toestemming voor in. Andere ervaring of factureringsaccount-lezingen kunnen deze weigering niet omzeilen.

### [Controleer of het factureringsaccount kan betalen](#controleer-of-het-factureringsaccount-kan-betalen)[](#controleer-of-het-factureringsaccount-kan-betalen)

Als het betaaltype dat de gebruiker vroeg niet beschikbaar is, geef de gebruiker paymentSetupUrl  of de betalingsfout's actionUrl . Stop met het maken van de campagne totdat ze de setup hebben voltooid of een ander betaaltype kiezen. Wissel geen betaaltypes zonder te vragen, zelfs niet wanneer het account READY  is met advertentietegoed. Los deze betalingskeuze op voordat je creatieven controleert of registreert.

Een campagne heeft één betaaltype nodig dat het kan financieren: een geverifieerde kaart, of genoeg advertentietegoed voor het budget van de eerste dag. Voor een groepsaccount, zie [Adverteer een groepservaring](#adverteer-een-groepservaring) . Betaalmethoden die het account niet heeft zijn optioneel. Ze blokkeren geen campagne.

Voordat je een campagne maakt, roep campaign-options  aan met universeId , of krijg het factureringsaccount:

Krijg een factureringsaccount

```

curl --location 'https://apis.roblox.com/ads-management/v1/billing-accounts/${BillingAccountId}' \

--header 'x-api-key: ${ApiKey}'

```

Voor het geselecteerde account, lees supportedPaymentTypes  (paymentTypes  in campaign-options ), paymentStatus , paymentStatusReason , en paymentSetupUrl . Kies een betaaltype uit supportedPaymentTypes . Als de gebruiker geen betaaltype noemt en er maar één is vermeld, gebruik deze. Als er meerdere zijn vermeld, toon ze aan de gebruiker en laat de gebruiker kiezen.

| paymentStatus | | paymentStatusReason | | Betekenis | | Actie van de gebruiker in Ads Manager |
| READY | | Afwezig | | Ten minste één betaaltype in supportedPaymentTypes  kan een campagne financieren. | | Geen actie vereist. paymentSetupUrl , wanneer aanwezig, biedt een optionele betaalmethode of advertentietegoed. |
| ACTION_REQUIRED | | NO_PAYMENT_METHOD | | Geen betaaltype kan een campagne financieren: geen bruikbare kaart en geen bruikbaar advertentietegoed. | | Voeg een kaart toe of koop advertentietegoed met paymentSetupUrl . |
| ACTION_REQUIRED | | PROFILE_NOT_VERIFIED | | Geen bruikbaar advertentietegoed, en de kaart op bestand moet worden geverifieerd, inclusief een lopende uitdaging. | | Voltooi de kaartverificatie met paymentSetupUrl . |
| PAST_DUE | | TRANSACTION_FAILURE | | Een kaartbetaling is mislukt of een mislukte kosten zijn onbetaald. Een mislukte kaartbetaling verwijdert CREDIT_CARD  uit supportedPaymentTypes . | | Los de betaling op in Betalingsinstellingen met paymentSetupUrl . |
| DISABLED | | ACCOUNT_DISABLED | | Het account is uitgeschakeld of gearchiveerd. supportedPaymentTypes  is leeg. | | Betalingssetup kan deze status niet verhelpen, en er wordt geen setup-link geretourneerd. |

Creëren kan alleen slagen met een betaaltype dat in supportedPaymentTypes  staat: altijd voor READY , soms voor PAST_DUE , en nooit voor ACTION_REQUIRED  of DISABLED . Andere campagnecontroles blijven van toepassing.

Budgetlimieten voor elk betaaltype:

-

ADS_CREDIT  wordt vermeld wanneer advertentietegoed is geactiveerd en het saldo ten minste het minimum dagelijkse budget is. Creëren en campaigns:validate  controleren ook of het saldo, na onbetaalde uitgaven, het dagelijkse budget dekt. Voor een LIFETIME  budget is het dagelijkse budget het bedrag gedeeld door het aantal campagnedagen.

-

Voor CREDIT_CARD  mag het dagelijkse budget niet meer zijn dan billingAccounts[].maximumDailyBudgetMicros  van campaign-options . CREDIT_CARD  wordt alleen vermeld wanneer die limiet ten minste het minimum dagelijkse budget is. Een geverifieerde kaart met een lagere limiet retourneert nog steeds de limiet, maar het toevoegen van een kaart helpt niet. Gebruik in plaats daarvan advertentietegoed.

De limits  op een factureringsaccount zijn alleen van toepassing op CREDIT_CARD :

-

limits.maximumDailyBudgetMicros  is de dagelijkse budgetlimiet voor kaartcampagnes, dezelfde waarde als maximumDailyBudgetMicros  in campaign-options .

-

limits.billingThresholdMicros  is hoe vaak de kaart wordt gefactureerd: wanneer onbetaalde kaartuitgaven, in outstandingBalanceMicros , dit bedrag bereiken, rekent Roblox de kaart aan. Het account kan het teruggeven voordat er een kaart op bestand is.

Geen van beide limieten is van toepassing op ADS_CREDIT  campagnes. Een advertentietegoedcampagne besteedt van het saldo, en de limiet is het saldo.

#### [Betalingsfouten](#betalingsfouten)[](#betalingsfouten)

Creëren en campaigns:validate  retourneren deze betalingsfouten. campaigns:validate  retourneert ze in errors[]  met valid: false .

| Verzoek | | reden | | veld |
| CREDIT_CARD  zonder een geverifieerde kaart, of met een mislukte betaling | | PAYMENT_ACTION_REQUIRED | | billingAccountId |
| ADS_CREDIT  met een saldo onder het dagelijkse budget | | INSUFFICIENT_AD_CREDIT | | budget.amountMicros |
| ADS_CREDIT  zonder geactiveerd advertentietegoed | | PAYMENT_ACTION_REQUIRED | | paymentType |

Elke fout heeft een actionUrl . Wanneer een van deze fouten optreedt, controleer eerst of een ander betaaltype in supportedPaymentTypes  de campagne kan financieren, of dat een lager budget past bij het saldo. Bied die opties aan de gebruiker samen met de link.

#### [Stuur de gebruiker naar Ads Manager](#stuur-de-gebruiker-naar-ads-manager)[](#stuur-de-gebruiker-naar-ads-manager)

Stuur de gebruiker alleen naar Ads Manager in deze gevallen:

-

De gebruiker vraagt om een betaalmethode die het account niet heeft.

-

paymentStatus  is ACTION_REQUIRED , zodat geen betaaltype een campagne kan financieren.

-

Creëren of campaigns:validate  retourneert een betalingsfout, en de gebruiker wil deze oplossen in Ads Manager.

Dan:

1.

Toon paymentSetupUrl , of de fout's actionUrl , aan de gebruiker.

2.

Vraag de gebruiker om Ads Manager te openen en de betalingsactie in de browser te voltooien.

3.

Wacht tot de gebruiker antwoordt dat ze klaar zijn.

4.

Controleer GET /billing-accounts/{id}  of campaigns:validate  opnieuw.

5.

Ga verder wanneer het geselecteerde betaaltype in supportedPaymentTypes  staat.

De browser vertelt de agent niet wanneer de setup is voltooid. Probeer de betalingssetup niet steeds opnieuw terwijl je wacht op het antwoord van de gebruiker. Verzamel nooit kaartnummers of andere betalingsgegevens via de API of in de chat.

Kaarten zijn alleen beschikbaar voor persoonlijke accounts, en alleen voor gebruikers die 18 jaar of ouder zijn. Groepsadvertentietegoedlinks bevatten groupId .

Om te zien hoeveel advertentietegoed een bedrag aan Robux koopt, stuur POST /billing-accounts/{id}/ad-credit-conversions:preview  voor het factureringsaccount. Gebruik een id  van GET /billing-accounts , niet een campagne- of groeps-ID. Een 404  NOT_FOUND  betekent dat het pad verkeerd is, of dat het factureringsaccount niet bestaat of toebehoort aan een andere gebruiker. Stuur robuxAmount  of adCreditAmountMicros , en de preview berekent het andere bedrag. De preview converteert niets. Als het account het bedrag niet kan betalen, is de respons 200  met valid: false  en een reden , en het toont nog steeds beide bedragen. Gebruik ze om de gebruiker te vertellen hoeveel ze nodig hebben.

### [Schat resultaten (optioneel)](#schat-resultaten-optioneel)[](#schat-resultaten-optioneel)

Deze bewerkingen zijn niet-bindend en creëren niets:

-

campaign-recommendations  suggereert een dagelijks budget en een duur.

-

performance-estimates  schat de resultaten van een budget, of het budget voor een doelresultaat. Het ondersteunt alleen PLAYS .

-

audience-estimates  schat hoeveel gebruikers je targeting kan bereiken.

audience-estimates  accepteert dezelfde targeting  als campagnecreatie, met dezelfde regels. campaign-recommendations  accepteert alleen targeting.audienceType : RETENTION  en REACTIVATION  krijgen een budget voor dat publiek. Andere targetingvelden in een aanbevelingsverzoek retourneren 400 .

## [Bereid creatieven voor](#bereid-creatieven-voor)[](#bereid-creatieven-voor)

Elke creatieve is een afbeeldingsactief dat je bezit of kunt gebruiken.

### [Gebruik een bestaande afbeelding](#gebruik-een-bestaande-afbeelding)[](#gebruik-een-bestaande-afbeelding)

Als de gebruiker afbeeldingsactief-ID's verstrekt die al zijn geüpload en volledig zijn verwerkt, geef ze door in creativeAssetIds  wanneer je de campagne maakt. Het creëren van een campagne registreert zijn activa in de bibliotheek van het factureringsaccount, zodat je de afbeeldingen niet opnieuw hoeft te uploaden of eerst POST /creatives  hoeft aan te roepen.

Een afbeeldingsactief hoeft niet in een bibliotheek te staan voordat je het gebruikt. GET /creatives  lijst alleen de afbeeldingen die al zijn geregistreerd in dat account. Als een geüpload afbeeldingsactief niet in die lijst staat, kun je nog steeds de activa-ID doorgeven in creativeAssetIds . Een lokaal afbeeldingsbestand is nog geen actief. Upload het eerst, zoals in [Upload een nieuwe afbeelding](#upload-een-nieuwe-afbeelding) .

Roep POST /creatives  alleen aan wanneer de gebruiker vraagt om een afbeelding aan de bibliotheek toe te voegen zonder een campagne te creëren. Voeg groupId  toe voor een groepsaccount. Registratie uploadt geen afbeelding.

Voeg een actief toe aan de creatieve bibliotheek

```

curl --location 'https://apis.roblox.com/ads-management/v1/creatives' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{ "assetId": "${AssetId}", "universeId": "${UniverseId}" }'

```

Om moderatie te controleren, krijg de creatieve met GET /creatives/{id}  en lees moderationStatus . Het is PENDING_REVIEW  totdat de beoordeling is voltooid.

### [Upload een nieuwe afbeelding](#upload-een-nieuwe-afbeelding)[](#upload-een-nieuwe-afbeelding)

Als de gebruiker een nieuw afbeeldingsactief nodig heeft:

1.

Upload de afbeelding via de [Assets API](/docs/nl-nl/cloud/guides/usage-assets)  met assetType  Image . Voor de beste pasvorm in de tegel, gebruik een aanbevolen grootte uit adFormats  in campaign-options . adFormats  is een aanbeveling, geen vereiste.

2.

Poll de uploadbewerking totdat deze is voltooid, en registreer de assetId .

3.

Geef de activa-ID door in creativeAssetIds  wanneer je de campagne maakt.

De API leest width  en height  van de afbeelding wanneer deze de creatieve registreert. Als het deze niet kan lezen, bijvoorbeeld omdat de upload nog wordt verwerkt, heeft de creatieve geen width  of height .

Creatieven hebben twee ID's:

-

assetId  is de Roblox activa-ID. Gebruik deze in creativeAssetIds , en in de GET /creatives/{id}  en PATCH /creatives/{id}  paden.

-

id  is de UUID van de registratie in de bibliotheek. Geen pad gebruikt deze.

Bijvoorbeeld, een bibliotheekvermelding met id: "a672e5b4-790b-4fa8-90de-6e7d2d60c83b"  en assetId: "1234567890"  gebruikt GET /creatives/1234567890 . Het verzenden van de UUID retourneert 404 .

Als het actief al actief is in hetzelfde account, retourneert POST /creatives  409  ALREADY_EXISTS . Als het actief in dat account is gearchiveerd, herstelt POST /creatives  het. Je kunt hetzelfde actief registreren in je persoonlijke account en in groepsaccounts.

GET /creatives  lijst de bibliotheek van één account. Voeg universeId  toe om alleen de creatieven van één ervaring te lijst. Met groupId  en universeId  samen, heb je toestemming nodig om te adverteren voor de groep en voor de ervaring. Voor een actief dat niet bestaat, of een account dat je niet kunt openen, retourneert GET /creatives/{id}  dezelfde 404 .

## [Maak een campagne](#maak-een-campagne)[](#maak-een-campagne)

### [Valideer het verzoek (optioneel)](#valideer-het-verzoek-optioneel)[](#valideer-het-verzoek-optioneel)

campaigns:validate  voert elke controle uit die creatie uitvoert, maar creëert niets. Het retourneert alle problemen in één antwoord, en het factureringsaccount waar het verzoek naar verwijst. Gebruik het om een campagne te controleren voordat de gebruiker klaar is om deze te lanceren.

Stuur een JSON-verzoeklichaam met de campagnevelden, net zoals voor creatie. Een POST zonder lichaam retourneert 400  met "Request body is required." Lees de documentatie van het eindpunt om de velden te ontdekken; probeer het niet met een lege POST.

Valideer een campagne

```

curl --location 'https://apis.roblox.com/ads-management/v1/campaigns:validate' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "name": "Zomer promo",

    "objective": "PLAYS",

    "paymentType": "ADS_CREDIT",

    "targetUniverseId": "${UniverseId}",

    "creativeAssetIds": ["${AssetId}"],

    "budget": { "type": "DAILY", "amountMicros": "20000000" },

    "schedule": { "startTime": "2026-12-01T00:00:00Z", "durationInDays": 7 }

}'

```

Een 200  respons betekent alleen dat de validatie is uitgevoerd. Lees valid , errors , warnings , en resolvedBillingAccountId . De errors  zijn dezelfde fouten die creatie zou retourneren.

### [Stuur het aanmaakverzoek](#stuur-het-aanmaakverzoek)[](#stuur-het-aanmaakverzoek)

1.

Voor retry deduplicatie, maak een nieuwe UUID en stel idempotencyKey  in het verzoeklichaam in.

2.

Stel de doelstelling en het betaaltype in van campaign-options .

3.

Stel targetUniverseId , creativeAssetIds , budget , en schedule  in.

4.

Voor een groepsaccount, stel billingAccountId  in. Zie [Adverteer een groepservaring](#adverteer-een-groepservaring) .

5.

Stuur het verzoek.

Maak een campagne

```

curl --location 'https://apis.roblox.com/ads-management/v1/campaigns' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "idempotencyKey": "${UUID}",

    "name": "Zomer promo",

    "objective": "PLAYS",

    "paymentType": "ADS_CREDIT",

    "targetUniverseId": "${UniverseId}",

    "creativeAssetIds": ["${AssetId}"],

    "budget": { "type": "DAILY", "amountMicros": "20000000" },

    "schedule": { "startTime": "2026-12-01T00:00:00Z", "durationInDays": 7 },

    "targeting": { "ageGroups": ["AGE_18_24", "AGE_25_PLUS"], "devices": ["PHONE", "TABLET"] }

}'

```

Respons (200 OK, fragment)

```

{

  "id": "7225a97c-4f1e-4b8a-9c3d-2e5f6a7b8c9d",

  "status": "ACTIEF",

  "deliveryStatus": "NOT_SERVING",

  "deliveryStatusReasons": ["SCHEDULED"]

}

```

Vergeet deze regels voor het verzoek niet:

-

Budget.  amountMicros  moet ten minste het minimum in budgetConstraints  zijn. budget.type  is DAILY  of LIFETIME , en je kunt het later niet wijzigen.

-

Schema.  startTime  mag niet in het verleden zijn. Stel de lengte in met durationInDays , tot 3650 . endTime  is alleen-lezen, en een verzoek dat deze bevat retourneert 400 . De campagne eindigt één seconde voor middernacht, in de tijdzone van het account, aan het einde van de laatste dag.

-

Targeting.  Laat targeting  weg, of stuur een leeg object, om alle doelgroepen te bereiken. Een lege array in een dimensie betekent alle waarden. Gebruik alleen de waarden in targetingDimensions . Voor ENGAGEMENT , laat targeting  weg of stel alleen audienceType  in op ALL_PLAYERS .

-

Regio's en landen.  Gebruik targeting.countries  voor enkele landen, en targeting.regions  voor aggregaatregio's, zoals WESTERN_EUROPE  of ROW . Combineer de regio ALL  niet met landen, en noem een land niet samen met de regio die het bevat.

### [Gebruik een nieuwe idempotency-sleutel voor elk nieuw verzoeklichaam](#gebruik-een-nieuwe-idempotency-sleutel-voor-elk-nieuw-verzoeklichaam)[](#gebruik-een-nieuwe-idempotency-sleutel-voor-elk-nieuw-verzoeklichaam)

POST /campaigns  accepteert een optioneel idempotencyKey  lichaam veld. Als je een niet-lege waarde opgeeft, moet deze een UUID bevatten.

Als je idempotencyKey  weglaat of een lege string verzendt, creëert de API zonder deduplicatie. Een retry kan een andere campagne creëren.

Voor retry deduplicatie, maak een nieuwe UUID voor elke nieuwe campagne of gewijzigd verzoeklichaam, inclusief wijzigingen in de naam. Gebruik dezelfde sleutel alleen om hetzelfde lichaam opnieuw te proberen, bijvoorbeeld na een time-out.

Voor 24 uur retourneert de sleutel van een voltooide aanvraag de originele campagne met 200 . Als je het lichaam wijzigt en dezelfde sleutel opnieuw gebruikt, retourneert de API de originele campagne en past je wijzigingen niet toe. De API retourneert geen 409  voor deze situatie, dus een 200  respons bevestigt je wijzigingen niet. Als het eerste verzoek nog in behandeling is, retourneert een retry 429 . Om een campagne die bestaat te wijzigen, gebruik PATCH /campaigns/{id} .

### [Voeg een video toe](#voeg-een-video-toe)[](#voeg-een-video-toe)

Een gesponsorde tegel kan de previewvideo van de ervaring tonen in plaats van de afbeelding. De video is altijd de previewvideo van de ervaring. Je kunt geen video voor een campagne uploaden.

1.

Roep campaign-options  aan met universeId .

2.

Als video.sources  PREVIEW_VIDEO  bevat, is video beschikbaar. Als video  afwezig is, gebruik dan een afbeelding-only campagne.

3.

Lees video.previewVideo . Als available  false  is, heeft de ervaring momenteel geen previewvideo, en toont de tegel de afbeelding.

4.

Voeg "video": { "source": "PREVIEW_VIDEO" }  toe aan het aanmaakverzoek. Houd creativeAssetIds : de afbeeldingen zijn nog steeds vereist.

Videobeschikbaarheid hangt af van het factureringsaccount. campaign-options  toont video  wanneer ten minste één van je factureringsaccounts dit toestaat. Als het factureringsaccount van de campagne geen video toestaat, retourneren creëren en bijwerken 400 . De campagne-respons toont de video in video.source  en video.previewVideoAssetId .

### [Adverteer een groepservaring](#adverteer-een-groepservaring)[](#adverteer-een-groepservaring)

Een campagne voor een groepservaring kan je persoonlijke account of het groepsaccount gebruiken. Als je billingAccountId  weglaat, gebruikt de API je persoonlijke account, ook voor een groepservaring. Om te betalen met het advertentietegoed van de groep:

1.

Roep campaign-options  aan met de universeId  van de ervaring.

2.

Vind het account van de groep in billingAccounts .

3.

Stel billingAccountId  in op de id  van dat account, en paymentType  op ADS_CREDIT .

Een groepsaccount accepteert alleen ADS_CREDIT , en alleen voor ervaringen die de groep bezit. Toestemming om voor de groep te adverteren is voldoende om een campagne ermee te creëren. Het kopen van groepsadvertentietegoed, of het instellen van autoReloadAdCreditEnabled  op true  voor een campagne die door het groepsaccount wordt betaald, vereist de spendGroupFunds  toestemming.

Groepsleden die de ervaring kunnen adverteren, kunnen de campagnes van de groep lezen en bijwerken zonder groupId , en ze kunnen het budget van een campagne die door het groepsaccount wordt betaald verhogen. Voor een campagne die door een persoonlijk account wordt betaald, kan alleen de eigenaar van dat account de uitgaven verhogen.

## [Volg beoordeling en levering](#volg-beoordeling-en-levering)[](#volg-beoordeling-en-levering)

Een nieuwe campagne ondergaat een beoordeling van het advertentiebeleid. Als startTime  in de toekomst ligt, is deliveryStatus  NOT_SERVING  met reden SCHEDULED  totdat de campagne begint, zoals in het bovenstaande voorbeeld. Als de campagne nu begint, is deliveryStatus  IN_REVIEW  totdat de beoordeling is voltooid.

Poll tot 100 campagnes in één oproep met campaigns:batchGetStatus :

Batch krijg campagne status

```

curl --location 'https://apis.roblox.com/ads-management/v1/campaigns:batchGetStatus' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{ "campaignIds": ["7225a97c-4f1e-4b8a-9c3d-2e5f6a7b8c9d"] }'

```

De respons heeft één vermelding in statuses  voor elke campagne, met status , deliveryStatus , en deliveryStatusReasons . ID's die niet bestaan, of die je niet kunt beheren, staan in een failures  array met reden NOT_FOUND .

| deliveryStatus | | Betekenis | | Veelvoorkomende deliveryStatusReasons |
| IN_REVIEW | | Beoordeling van het advertentiebeleid of setup is niet compleet. | | — |
| SERVING | | De campagne is actief. | | LEARNING  terwijl de levering toeneemt |
| NOT_SERVING | | De campagne is momenteel niet actief. | | SCHEDULED , PAUSED , INSUFFICIENT_AD_CREDIT , QPP_AUTO_PAUSED , COMPLETED , EXPIRED , CANCELLED , INACTIVE |
| REJECTED | | Beoordeling heeft de campagne of zijn ervaring afgewezen. | | MODERATED , CLICK_BAIT , GAME_FILTERED , PRIVATE , PLACE_JOIN_RESTRICTED |

Om het beoordelingsresultaat voor elke creatieve te zien, lijst de advertenties van de campagne met GET /campaigns/{campaignId}/ads . Elke advertentie heeft een reviewStatus , een deliveryStatus , en reviewIssues  wanneer de beoordeling een probleem vindt.

## [Beheer een campagne](#beheer-een-campagne)[](#beheer-een-campagne)

Gebruik PATCH /campaigns/{id}  en stuur alleen de velden die je wijzigt.

Pauzeer een campagne

```

curl --location --request PATCH 'https://apis.roblox.com/ads-management/v1/campaigns/7225a97c-4f1e-4b8a-9c3d-2e5f6a7b8c9d' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{ "status": "PAUSED" }'

```

| Wijziging | | Body | | Opmerkingen |
| Pauzeer | | { "status": "PAUSED" } | |  |
| Herstart | | { "status": "ACTIVE" } | |  |
| Annuleer | | { "status": "CANCELLED" } | | Permanent. Een andere annuleringsaanvraag retourneert de campagne onveranderd. |
| Hernoem | | { "name": "..." } | |  |
| Wijzig budget | | { "budget": { "amountMicros": "..." } } | | Een verhoging wordt onmiddellijk toegepast. Een verlaging op een actieve campagne wordt toegepast bij de volgende middernacht in de tijdzone van het account. Tot dan tonen budget.scheduledAmountMicros  en budget.scheduledEffectiveTime  de verwachte verlaging. |
| Wijzig schema | | { "schedule": { "startTime": "...", "durationInDays": 14 } } | | Alleen voordat de campagne begint. |
| Voeg creatieven toe | | { "creativeAssetIds": ["..."] } | | De API voegt nieuwe ID's toe en negeert ID's die de campagne al heeft. |
| Wijzig video | | { "video": { "source": "IMAGE_ONLY" } } | | Van toepassing op elke advertentie. Alleen wanneer mutableFields  in campaign-options  video  opsomt. |

PATCH  kan een creatieve niet uit een campagne verwijderen. Om een veld te wijzigen dat mutableFields  niet opsomt, maak een nieuwe campagne. Om één creatieve te stoppen, pauzeer je advertentie:

Pauzeer één advertentie

```

curl --location --request PATCH 'https://apis.roblox.com/ads-management/v1/campaigns/7225a97c-4f1e-4b8a-9c3d-2e5f6a7b8c9d/ads/${AdId}' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{ "status": "PAUSED" }'

```

Om een creatieve te archiveren met PATCH /creatives/{id} , stuur isArchived: true  als het enige veld. Als een ingeschakelde advertentie de creatieve gebruikt, retourneert het verzoek 409  FAILED_PRECONDITION . Pauzeer eerst de advertentie. Voor andere mislukte bewerkingen, zie [Fouten afhandelen](#fouten-afhandelen) .

## [Lijst bronnen](#lijst-bronnen)[](#lijst-bronnen)

Lijst-eindpunten gebruiken cursor-paginering met maxPageSize  en pageToken .

Belangrijk:  Een pagina kan kort of leeg zijn terwijl er meer resultaten blijven. Ga door totdat de respons geen nextPageToken  heeft. Stop niet bij de eerste lege pagina.

-

GET /campaigns  lijst de campagnes van je persoonlijke account. Voeg groupId  toe voor een groepsaccount.

-

Om de campagnes van specifieke ervaringen over alle accounts te lijst, gebruik targetUniverseIds  in plaats van groupId . Herhaal de parameter voor elke ID, tot 10: targetUniverseIds=1&targetUniverseIds=2 . Een door komma's gescheiden lijst retourneert 400 .

-

Houd dezelfde filters op elke pagina van een lijst.

## [Rapporteren over prestaties](#rapporteren-over-prestaties)[](#rapporteren-over-prestaties)

Query de prestaties van Gesponsorde Advertenties voor een ervaring via de [Analytics Query API](/docs/nl-nl/cloud/guides/analytics) . Gebruik SponsoredAdsClicks , SponsoredAdsImpressions , en SponsoredAdsSpendUsd  met OneHour , OneDay , of None  granulariteit. SponsoredAdsSpendUsd  retourneert uitgaven in dollars.

De advertentie id  van GET /campaigns/{campaignId}/ads  komt overeen met de AdId  dimensie in analysemethoden. Zie [Ondersteunde metrics en dimensies](/docs/nl-nl/cloud/guides/analytics/metrics)  voor meer Analytics Query API-metrics.

Wanneer je campagnes vergelijkt:

-

Beoordeel elke doelstelling op het resultaat waarvoor deze optimaliseert. De metrics van Gesponsorde Advertenties rapporteren klikken, vertoningen en uitgaven, niet afspeelacties of latere acties, dus kosten per klik zijn slechts een proxy. ENGAGEMENT  en ROBUX_SPEND  campagnes optimaliseren voor acties na de klik, dus ze kosten meestal meer per klik. Kies niet tussen doelstellingen op basis van kosten per klik alleen.

-

Beoordeel een campagne niet terwijl deliveryStatusReasons  LEARNING  bevat. Levering en kosten veranderen terwijl het toeneemt. Vergelijk campagnes over dezelfde data, nadat ze allemaal de leerfase hebben verlaten.

## [Fouten afhandelen](#fouten-afhandelen)[](#fouten-afhandelen)

De Ads API retourneert fouten in deze envelop:

Foutrespons (400)

```

{

  "status": 400,

  "title": "Ongeldig verzoek",

  "detail": "budget.amountMicros moet ten minste 5000000 zijn (minimum campagnebudget).",

  "errors": [

    {

      "code": "INVALID_ARGUMENT",

      "reason": "BELOW_MINIMUM",

      "field": "budget.amountMicros",

      "message": "budget.amountMicros moet ten minste 5000000 zijn (minimum campagnebudget).",

      "remediation": "Gebruik campaign-options budgetConstraints voor het huidige minimum."

    }

  ]

}

```

Wanneer verschillende velden niet geldig zijn, heeft elk veld zijn eigen vermelding in errors . Gebruik code  en reason  in je code, field  om het probleem te vinden, en remediation  om de gebruiker te vertellen wat te doen. Als retryable  true  is, kun je het verzoek opnieuw verzenden.

| Status | | code | | Veelvoorkomende oorzaken |
| 400 | | INVALID_ARGUMENT | | Een veld ontbreekt of is niet geldig. Lees reason , bijvoorbeeld BELOW_MINIMUM , UNSUPPORTED_VALUE , UNKNOWN_FIELD , IMMUTABLE_FIELD , of een [betalingsfout](#betalingsfouten) . |
| 400 | | FAILED_PRECONDITION | | De campagne of advertentie bevindt zich in een staat die de wijziging niet toestaat, bijvoorbeeld geannuleerd, beëindigd, of verwijderd. |
| 403 | | PERMISSION_DENIED | | Je kunt het account, de ervaring, of de creatieve niet gebruiken. Redenen zijn onder andere UNIVERSE_NOT_ADVERTISABLE  en BILLING_ACCOUNT_REQUIRED . |
| 404 | | NOT_FOUND | | De bron bestaat niet, of je kunt er geen toegang toe krijgen. De API retourneert dezelfde respons voor beide. |
| 409 | | ALREADY_EXISTS | | De creatieve is al in de bibliotheek van het account. |
| 409 | | FAILED_PRECONDITION | | De creatieve wordt gebruikt door een ingeschakelde advertentie. Pauzeer of archiveer de advertentie, en archiveer dan de creatieve. |
| 409 | | ABORTED | | Een andere schrijfbewerking heeft de bron gewijzigd. Verkrijg deze opnieuw en probeer het opnieuw. |
| 429 | | RESOURCE_EXHAUSTED | | Te veel verzoeken, of een retry van een aanmaakverzoek dat nog in behandeling is. Wacht, en probeer het opnieuw met backoff. |
| 500, 503, 504 | | INTERNAL_ERROR , UNAVAILABLE , DEADLINE_EXCEEDED | | Een server- of afhankelijkheidsfout. Probeer het opnieuw met backoff. |

De API-gateway controleert de API-sleutel en scopes voordat het verzoek naar de Ads API gaat. Deze fouten gebruiken de envelop niet. Bijvoorbeeld, een API-sleutel die niet geldig is retourneert 401  met dit lichaam:

```

{ "errors": [{ "code": 0, "message": "Ongeldige API-sleutel" }] }

```

Een verzoek zonder referenties retourneert 403  met de boodschap Ongeldige authenticatiegegevens verstrekt .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
