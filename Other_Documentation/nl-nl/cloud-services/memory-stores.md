<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/memory-stores -->

Geheugenopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)

# Geheugenopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  is een data service met hoge doorvoer en lage latentie die snelle in-memory gegevensopslag biedt die toegankelijk is vanaf alle servers in een live sessie. Geheugenopslag  is geschikt voor frequente en ephemerale gegevens die snel veranderen en niet duurzaam hoeven te zijn, omdat ze sneller toegankelijk zijn en verdwijnen wanneer ze de maximale levensduur bereiken. Voor gegevens die moeten blijven bestaan tussen sessies, gebruik [gegevensopslag](/docs/nl-nl/cloud-services/data-stores) .

## [Gegevensstructuren](#gegevensstructuren)[](#gegevensstructuren)

In plaats van direct toegang te krijgen tot ruwe gegevens, hebben geheugenopslag drie primitieve gegevensstructuren die over servers worden gedeeld voor snelle verwerking: [gesorteerde kaart](/docs/nl-nl/cloud-services/memory-stores/sorted-map) , [wachtrij](/docs/nl-nl/cloud-services/memory-stores/queue)  en [hash kaart](/docs/nl-nl/cloud-services/memory-stores/hash-map) . Elke gegevensstructuur is geschikt voor bepaalde gebruikssituaties:

-

Vaardigheidsgebaseerde matchmaking  - Sla gebruikersinformatie, zoals vaardigheidsniveau, op in een gedeelde wachtrij  tussen servers en gebruik lobbyservers om periodiek matchmaking uit te voeren.

-

Cross-server handelen en veilen  - Maak universeel handelen mogelijk tussen verschillende servers, waar gebruikers kunnen bieden op items met real-time veranderende prijzen, met een gesorteerde kaart  van sleutel-waarde paren.

-

Wereldwijde ranglijsten  - Sla gebruikersrangschikkingen op en werk deze bij op een gedeelde ranglijst binnen een gesorteerde kaart .

-

Gedeelde inventarissen  - Sla inventarisitems en statistieken op in een gedeelde hash kaart , waar gebruikers inventarisitems gelijktijdig met elkaar kunnen gebruiken.

-

Cache voor persistente gegevens  - Synchroniseer en kopieer je persistente gegevens in een gegevensopslag naar een geheugenopslag hash kaart  die als cache kan fungeren en de prestaties van je game kan verbeteren.

Over het algemeen, als je gegevens op basis van een specifieke sleutel moet benaderen, gebruik dan een hash kaart. Als je wilt dat die gegevens geordend zijn, gebruik dan een gesorteerde kaart. Als je je gegevens in een specifieke volgorde moet verwerken, gebruik dan een wachtrij.

## [Limieten en quotum](#limieten-en-quotum)[](#limieten-en-quotum)

Om de schaalbaarheid en systeemprestaties te behouden, hebben geheugenopslag gegevensgebruikquota voor de geheugengrootte, API-aanvragen en de grootte van de gegevensstructuur.

Geheugenopslag heeft een uitzettingsbeleid op basis van vervaltijd, ook wel bekend als tijd tot leven (TTL). Items worden verwijderd nadat ze zijn verlopen, en het geheugenkotum wordt vrijgemaakt voor nieuwe invoer. Wanneer je de geheugengrens bereikt, mislukken aanvragen die het geheugengebruik verhogen totdat je geheugen vrijmaakt of je quotum verhoogt. Zie [Herstellen van geheugenquota-uitputting](#herstellen-van-geheugenquota-uitputting)  voor opties.

### [Geheugengroottequotum](#geheugengroottequotum)[](#geheugengroottequotum)

Het geheugenkotum beperkt de totale hoeveelheid geheugen die een game kan verbruiken. Het is geen vaste waarde; in plaats daarvan verandert het in de loop van de tijd afhankelijk van het aantal gebruikers in de game volgens de formule 64 KB + 1,2 KB * [aantal gebruikers] . Het quotum geldt op het niveau van de game in plaats van op het niveau van de server.

Wanneer gebruikers de game betreden, is het extra geheugenkotum onmiddellijk beschikbaar. Wanneer gebruikers de game verlaten, wordt het quotum niet onmiddellijk verlaagd. Er is een terugloopperiode van acht dagen voordat het quotum opnieuw wordt geëvalueerd naar een lagere waarde.

Nadat je game de geheugengroottequotum heeft bereikt, mislukken alle API-aanvragen die de geheugengrootte verhogen. Aanvragen die de geheugengrootte verlagen of niet veranderen, slagen nog steeds.

Met het [observability](/docs/nl-nl/cloud-services/memory-stores/observability)  dashboard kun je het geheugengroottequotum van je game in realtime bekijken met behulp van de Geheugenverbruik  grafiek.

### [API-aanvraaglimieten](#api-aanvraaglimieten)[](#api-aanvraaglimieten)

Een aanvraageenheid  quotum geldt voor alle [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  API-aanroepen. Dit quotum is 1000 + 120 * [aantal gelijktijdige gebruikers]  aanvraageenheden per minuut.

De meeste API-aanroepen verbruiken slechts één aanvraageenheid, met enkele uitzonderingen:

-

[MemoryStoreSortedMap:GetRangeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetRangeAsync)

Verbruikt eenheden op basis van het aantal geretourneerde items. Als deze methode bijvoorbeeld 10 items retourneert, telt de oproep als 10 aanvraageenheden. Als het een lege reactie retourneert, telt het als één aanvraageenheid.

-

[MemoryStoreQueue:ReadAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#ReadAsync)

Verbruikt eenheden op basis van het aantal geretourneerde items, net als MemoryStoreSortedMap:GetRangeAsync() , maar verbruikt een extra eenheid elke twee seconden tijdens het lezen. Geef de maximale leestijd op met de parameter waitTimeout .

-

[MemoryStoreHashMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)

Verbruikt minimaal twee eenheden.

-

[MemoryStoreHashMap:ListItemsAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync)

Verbruikt [aantal gescande partities] + [items geretourneerd]  eenheden.

Het aanvragenquotum geldt ook op het niveau van de game in plaats van op het niveau van de server. Dit biedt flexibiliteit om de aanvragen over servers te verdelen zolang de totale aanvraagfrequentie het quotum niet overschrijdt. Als je het quotum overschrijdt, ontvang je een foutreactie wanneer de service je aanvragen beperkt.

Met de [observability](/docs/nl-nl/cloud-services/memory-stores/observability)  functie kun je het aanvraageenheidquotum van je game in realtime bekijken.

### [Limieten voor de grootte van gegevensstructuren](#limieten-voor-de-grootte-van-gegevensstructuren)[](#limieten-voor-de-grootte-van-gegevensstructuren)

Voor een enkele gesorteerde kaart of wachtrij gelden de volgende grootte- en itemaantal limieten:

-

Maximale aantal items: 1.000.000

-

Maximale totale grootte (inclusief sleutels voor gesorteerde kaart): 100 MB

### [Per-partitie limieten](#per-partitie-limieten)[](#per-partitie-limieten)

Naast het game-niveau [aanvraageenheidquotum](#api-aanvraaglimieten) , past geheugenopslag aanvraaglimieten toe op elke partitie als een waarborg die de stabiliteit van de service voor alle games beschermt. Deze limieten zijn geen quotum dat aan je game is toegewezen, en ze zijn geen harde limiet op de doorvoer die je game kan bereiken. De volgende waarden zijn schattingen. Ze zijn geconfigureerd op de Roblox-backend en kunnen veranderen, dus ontwerp er niet tegen als vaste getallen.

Elke aanvraag telt mee voor de limiet van de [partitie](/docs/nl-nl/cloud-services/memory-stores/per-partition-limits#partities)  die het item bevat, ongeacht de gegevensstructuur. Je kunt momenteel verwachten dat throttling begint bij ongeveer 30.000 aanvraageenheden per minuut  voor een enkele partitie, dus streef ernaar om goed onder die snelheid te blijven. Hoeveel van die limiet een gegevensstructuur verbruikt, hangt af van hoe de items zijn verdeeld:

-

Gesorteerde kaarten en wachtrijen  bevinden zich elk op een enkele partitie, dus elke aanvraag aan een van deze gegevensstructuren telt mee voor dezelfde partitie limiet.

-

Hash kaarten  verspreiden hun items over veel partities, zodat verkeer verspreid over veel item sleutels zelden de limiet van een enkele partitie benadert.

Hash kaarten hebben een extra limiet op elke itemsleutel van ongeveer 5.000 schrijfaanvraageenheden per minuut  en 15.000 leesaanvraageenheden per minuut . Deze per-sleutel limiet geldt bovenop de per-partitie limiet, zodat een vaak benaderde sleutel beide kan raken. De per-sleutel limiet geldt alleen voor operaties met enkele sleutels: de leeslimiet geldt voor [MemoryStoreHashMap:GetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#GetAsync) , de schrijf limiet geldt voor [MemoryStoreHashMap:SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#SetAsync)  en [MemoryStoreHashMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#RemoveAsync) , en [MemoryStoreHashMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  telt mee voor zowel de lees- als schrijf limieten. [MemoryStoreHashMap:ListItemsAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync)  scant partities in plaats van een enkele sleutel, dus alleen de per-partitie limiet geldt voor deze.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Per-Partition-Limits-4.png)

Als je geen sortering of first-in, first-out functionaliteit nodig hebt, is een hash kaart meestal de beste keuze omdat deze de belasting over partities kan verspreiden.

Wanneer aanvragen de limiet van een partitie of per-sleutel overschrijden, beperkt de service deze en retourneert een PartitionRequestsOverLimit  statuscode, die je kunt volgen met het [observability](/docs/nl-nl/cloud-services/memory-stores/observability)  dashboard.

Als je verwacht dat een gegevensstructuur of een itemsleutel een hoge, aanhoudende aanvraagfrequentie zal ontvangen, [shard](/docs/nl-nl/cloud-services/memory-stores/best-practices#verdeel-de-belasting-met-sharding)  deze zodat de belasting over meer partities of sleutels verspreid wordt. Verspreid lezen en schrijven gelijkmatig over meerdere itemsleutels om binnen de per-sleutel limieten te blijven. Je kunt ook de aanvraagfrequentie verlagen door waarden op de server te cachen en deze na een interval opnieuw te controleren, aanvragen te bundelen waar mogelijk, en [exponentiële terugval](https://en.wikipedia.org/wiki/Exponential_backoff)  toe te passen wanneer je throttlingreacties ontvangt.

We streven ernaar zo transparant mogelijk te zijn over snelheidslimieten, maar er kunnen aanvullende, niet gedocumenteerde limieten van toepassing zijn, inclusief voor DDoS-bescherming en service-stabiliteit. Zorg er altijd voor dat je game throttlingreacties afhandelt. Zie [Probleemoplossing](#probleemoplossing)  voor richtlijnen.

Als je een niet gedocumenteerde snelheidslimiet tegenkomt die je gebruiksgeval blokkeert (of je zou hogere limieten willen), laat dan feedback achter waarin je je behoeften uitlegt in het [Developer Forum](https://devforum.roblox.com/) .

## [Herstellen van geheugenquota-uitputting](#herstellen-van-geheugenquota-uitputting)[](#herstellen-van-geheugenquota-uitputting)

Als je game TotalMemoryOverLimit  fouten ontvangt, controleer dan de Geheugenverbruik  grafiek in het [observability dashboard](/docs/nl-nl/cloud-services/memory-stores/observability) . Om het schrijven dat het geheugengebruik verhoogt te hervatten, verwijder onnodige items, wacht tot items verlopen, of gebruik een van de volgende opties.

### [Geheugenopslag flushen met Open Cloud](#geheugenopslag-flushen-met-open-cloud)[](#geheugenopslag-flushen-met-open-cloud)

Als je de opgeslagen gegevens niet meer nodig hebt, gebruik dan de Open Cloud [Flush Memory Store](/docs/nl-nl/cloud/reference/features/storage#Cloud_FlushMemoryStore)  eindpunt om asynchroon alle geheugenopslaggegevensstructuren in een universum voor de geselecteerde scope te wissen.

Een flush wist alle wachtrijen, gesorteerde kaarten en hash kaarten in de geselecteerde scope, niet alleen een individuele gegevensstructuur. Dit omvat gegevens die live functies zoals matchmaking of handelen mogelijk nog nodig hebben. Flush alleen wanneer je game kan functioneren zonder die gegevens.

Om geheugenopslag te flushen:

1.

[Maak een API-sleutel](/docs/nl-nl/cloud/auth/api-keys)  met machtigingen om geheugenopslag te flushen en de status van de flushbewerking voor het doeluniversum te krijgen.

2.

Stuur een POST  aanvraag naar https://apis.roblox.com/cloud/v2/universes/{universe_id}/memory-store:flush  met de API-sleutel in de x-api-key  header. Vervang {universe_id}  door de universum-ID van je game. Stel de scope  queryparameter in op LIVE  voor productiedata of TEST  voor Studio-gegevens. Als je scope  weglaat, gebruikt het eindpunt LIVE .

3.

Gebruik [Get Memory Store Flush Operation](/docs/nl-nl/cloud/reference/features/storage#Cloud_GetMemoryStoreFlushOperation)  om de operatie die door de flush-aanroep is geretourneerd te polsen totdat done  true  is, en controleer op een error . Gebruik dezelfde scope bij het polsen. Het geretourneerde path  bevat al cloud/v2 , dus pols op https://apis.roblox.com/{path}  zonder een andere prefix toe te voegen.

Studio- en productiememoryopslag zijn [geïsoleerd](#testen-en-debuggen-in-studio) . Het flushen van de ene scope wist de andere niet. Nadat je onnodige gegevens hebt gewist, volg je de [beste praktijken](#beste-praktijken) , zoals kortere vervaltijden en expliciete verwijdering, om te voorkomen dat het geheugengebruik opnieuw de quotum bereikt.

### [Verhoog capaciteit met Uitgebreide Diensten](#verhoog-capaciteit-met-uitgebreide-diensten)[](#verhoog-capaciteit-met-uitgebreide-diensten)

Als je game de gegevens moet behouden en meer opslag nodig heeft dan het standaardquotum toestaat, schakel dan [Uitgebreide Diensten](/docs/nl-nl/cloud-services/extended-services)  in voor geheugenopslag. Uitgebreide Diensten stelt je in staat om te betalen voor geheugenopslag en aanvragen boven de standaardquota.

Om te beginnen, voldoe aan de [geschiktheidseisen](/docs/nl-nl/cloud-services/extended-services#geschiktheidseisen) , voeg accountgegevens en een betaalmethode toe, en selecteer vervolgens je game in het [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Onder Uitgebreide Diensten , schakel geheugenopslag in en stel maandelijkse budgetten in voor de middelen die je nodig hebt. Zie [Een dienst inschakelen](/docs/nl-nl/cloud-services/extended-services#een-dienst-inschakelen)  en [Dienstenprijzen](/docs/nl-nl/cloud-services/extended-services#prijzen-van-diensten)  voor details.

Uitgebreide Diensten beperkt de service als het gebruik je budget overschrijdt. Houd het gebruik en de facturering in de gaten en blijf [onnodige gegevens verwijderen](#beste-praktijken) .

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

Om je geheugengebruikspatroon optimaal te houden en te voorkomen dat je de [limieten](#limieten-en-quotum)  overschrijdt, volg je deze beste praktijken:

-

Verwijder verwerkte items.  Consistent opruimen van gelezen items met behulp van de [MemoryStoreQueue:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#RemoveAsync)  methode voor wachtrijen en [MemoryStoreSortedMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#RemoveAsync)  voor gesorteerde kaarten kan geheugen vrijmaken en de gegevensstructuur up-to-date houden.

-

Stel de vervaltijd in op het kortste tijdsbestek dat mogelijk is bij het toevoegen van gegevens.  Hoewel de standaard vervaltijd 45 dagen is voor zowel [MemoryStoreQueue:AddAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#AddAsync)  als [MemoryStoreSortedMap:SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#SetAsync) , kan het instellen van de kortst mogelijke tijd automatisch oude gegevens opruimen om te voorkomen dat ze je geheugengebruikquotum vullen.

-

Bewaar geen grote hoeveelheid gegevens met een lange vervaltijd, omdat dit het risico met zich meebrengt dat je geheugenkotum wordt overschreden en mogelijk problemen veroorzaakt die je hele game kunnen breken.

-

Verwijder altijd expliciet onnodige items of stel een korte itemverval in.

-

Over het algemeen moet je expliciete verwijdering gebruiken voor het vrijgeven van geheugen en itemverval als een veiligheidsmechanisme om te voorkomen dat ongebruikte items gedurende een lange periode geheugen bezet houden.

-

Bewaar alleen noodzakelijke waarden in het geheugen.

Bijvoorbeeld, voor een veilinghuisgame hoef je alleen het hoogste bod bij te houden. Je kunt [MemoryStoreSortedMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync)  op één sleutel gebruiken om het hoogste bod bij te houden in plaats van alle biedingen in je gegevensstructuur te bewaren.

-

Gebruik [exponentiële terugval](https://en.wikipedia.org/wiki/Exponential_backoff)  om onder de API-aanvraaglimieten te blijven.

Bijvoorbeeld, als je een DataUpdateConflict  ontvangt, kun je het na twee seconden opnieuw proberen, dan vier, acht, enzovoort, in plaats van constant aanvragen naar [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  te sturen om de juiste reactie te krijgen.

-

Splits grote gegevensstructuren in meerdere kleinere door [sharding](https://en.wikipedia.org/wiki/Shard_(database_architecture)) .

Het is vaak gemakkelijker om gegevens in kleinere structuren te beheren dan alles in één grote gegevensstructuur op te slaan. Deze aanpak kan ook helpen om gebruiks- en snelheidslimieten te vermijden. Als je bijvoorbeeld een gesorteerde kaart hebt die prefixen voor zijn sleutels gebruikt, overweeg dan om elke prefix in zijn eigen gesorteerde kaart te scheiden. Voor een bijzonder populaire game kun je zelfs gebruikers in meerdere kaarten scheiden op basis van de laatste cijfers van hun gebruikers-ID's.

-

[Shard](/docs/nl-nl/cloud-services/memory-stores/best-practices)  vaak benaderde sleutels in hash kaarten met meerdere kopieën van de sleutel om de belasting te verdelen.

-

Comprimeer opgeslagen waarden.

Overweeg bijvoorbeeld om het [LZW](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Welch)  algoritme te gebruiken om de grootte van de opgeslagen waarde te verminderen.

-

Schrijf je in voor Uitgebreide Diensten.

Voor opslag of aanvraaggebruik dat verder gaat dan de standaardquota, [schakel Uitgebreide Diensten in voor geheugenopslag](#verhoog-capaciteit-met-uitgebreide-diensten) .

## [Observability](#observability)[](#observability)

Het [Observability Dashboard](/docs/nl-nl/cloud-services/memory-stores/observability)  biedt inzichten en analyses voor het monitoren en oplossen van problemen met je geheugenopslaggebruik. Met realtime bijgewerkte grafieken over verschillende aspecten van je geheugengebruik en API-aanvragen, kun je het geheugengebruikspatroon van je game volgen, de huidige toegewezen quota bekijken, de API-status monitoren en potentiële problemen identificeren voor prestatie-optimalisatie.

De volgende tabel geeft een overzicht van alle statuscodes van API-reacties die beschikbaar zijn op de Aanvraagtelling per Status  en Aanvragen per API x Status  grafieken van het Observability Dashboard. Voor meer informatie over hoe je deze fouten kunt oplossen, zie [Probleemoplossing](#probleemoplossing) . Voor het specifieke quotum of de limiet waar een fout betrekking op heeft, zie [Limieten en Quotum](#limieten-en-quotum) .

| Statuscode | | Beschrijving |
| --- | --- |
| Succes | | Succes. |
| DataStructureMemoryOverLimit | | Overschrijdt de geheugenlimiet op het niveau van de gegevensstructuur (100 MB). |
| DataUpdateConflict | | Conflict door gelijktijdige update. |
| AccessDenied | | Geen toestemming om gamegegevens te openen. Deze aanvraag verbruikt geen aanvraageenheden of gebruikt quotum. |
| InternalError | | Interne fout. |
| InvalidRequest | | De aanvraag heeft niet de vereiste informatie of heeft onjuiste informatie. |
| DataStructureItemsOverLimit | | Overschrijdt de limiet voor het aantal items op het niveau van de gegevensstructuur (1M). |
| NoItemFound | | Geen item gevonden in [MemoryStoreQueue:ReadAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#ReadAsync)  of [MemoryStoreSortedMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync) . ReadAsync()  pollt elke 2 seconden en retourneert deze statuscode totdat het items in de wachtrij vindt. |
| DataStructureRequestsOverLimit | | Overschrijdt de limiet voor aanvraageenheden op het niveau van de gegevensstructuur (100.000 aanvraageenheden per minuut). |
| PartitionRequestsOverLimit | | Overschrijdt een [per-partitie of per-sleutel aanvraageenheid limiet](#per-partition-limits) . |
| TotalRequestsOverLimit | | Overschrijdt de universele aanvraageenheid limiet. |
| TotalMemoryOverLimit | | Overschrijdt de universele geheugenkotum. |
| ItemValueSizeTooLarge | | Waarde grootte overschrijdt limiet (32 KB). |

De volgende tabel geeft statuscodes aan de clientzijde weer, die momenteel niet beschikbaar zijn op het Observability Dashboard.

| Statuscode | | Beschrijving |
| InternalError | | Interne fout. |
| UnpublishedPlace | | Je moet deze plaats publiceren om MemoryStoreService te gebruiken. |
| InvalidClientAccess | | MemoryStoreService moet vanaf de server worden aangeroepen. |
| InvalidExpirationTime | | Het veld 'verval' moet tussen 0 en 3.888.000 liggen. |
| InvalidRequest | | Kan waarde niet naar json converteren. |
| InvalidRequest | | Kan sortKey niet naar een geldig nummer of string converteren. |
| TransformCallbackFailed | | Kon transformatie callbackfunctie niet aanroepen. |
| RequestThrottled | | Recente MemoryStores-aanvragen hebben een of meer limieten bereikt. |
| UpdateConflict | | Maximaal aantal herhalingen overschreden. |

### [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

De volgende tabel geeft de aanbevolen oplossing voor elke responsstatuscode weer:

| Fout | | Probleemoplossingsopties |
| DataStructureRequestsOverLimit / PartitionRequestsOverLimit | |
-

Voeg een lokale cache toe door informatie op te slaan in een andere variabele en deze na een bepaalde tijdsinterval, zoals 30 seconden, opnieuw te controleren.

-

Gebruik de Aanvraagtelling per Status  grafiek om te verifiëren dat je meer Succes  reacties ontvangt dan NoItemFounds . Beperk het aantal keren dat je [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  aanroept met een mislukte aanvraag.

-

Implementeer een korte vertraging tussen aanvragen.

-

Volg de [beste praktijken](#beste-praktijken) , inclusief:

-

Shard je gegevensstructuren als je een aanzienlijke hoeveelheid DataStructureRequestsOverLimit / PartitionRequestsOverLimit  reacties ontvangt.

-

Shard je hash kaart sleutels als je een aanzienlijke hoeveelheid PartitionRequestsOverLimit  reacties ontvangt op hash kaart oproepen.

-

Verminder of bundel oproepen naar specifieke gegevensstructuren of hash kaart sleutels als je PartitionRequestsOverLimit  reacties ziet.

-

Implementeer een exponentiële terugval om een redelijke aanvraagfrequentie te vinden.

 |
| TotalRequestsOverLimit |
| DataStructureItemsOverLimit | |
-

Pas [beste praktijken](#beste-praktijken)  toe om de geheugengrootte te verminderen.

 |
| DataStructureMemoryOverLimit |
| TotalMemoryOverLimit | |
-

Verwijder onnodige items of wacht tot ze verlopen. Zie [beste praktijken](#beste-praktijken) .

-

Als je game kan functioneren zonder de opgeslagen gegevens, [flush geheugenopslag met Open Cloud](#geheugenopslag-flushen-met-open-cloud) .

-

Als je game meer opslag nodig heeft, [verhoog capaciteit met Uitgebreide Diensten](#verhoog-capaciteit-met-uitgebreide-diensten) .

 |
| DataUpdateConflict | |
-

Implementeer een korte vertraging tussen aanvragen om meerdere aanvragen te vermijden die dezelfde sleutel tegelijkertijd bijwerken.

-

Voor gesorteerde kaarten, gebruik de callbackfunctie op de [MemoryStoreSortedMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync)  methode om een aanvraag te annuleren na een bepaald aantal pogingen, zoals het volgende codevoorbeeld laat zien:

Voorbeeld van het Annuleren van een Aanvraag

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local map = MemoryStoreService:GetSortedMap("AuctionItems")

function placeBid(itemKey, bidAmount)

    map:UpdateAsync(itemKey, function(item)

        item = item or { highestBid = 0 }

        if item.highestBid < bidAmount then

            item.highestBid = bidAmount

            return item

        end

        print("item is "..item.highestBid)

        return nil

    end, 1000)

end

placeBid("MyItem", 50)

placeBid("MyItem", 40)

print("done")

```

-

Onderzoek of je [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  efficiënt aanroept om conflicten te vermijden. Idealiter zou je geen overmatige aanvragen moeten verzenden.

-

Verwijder consistent items zodra ze zijn gelezen met behulp van de [MemoryStoreQueue:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#RemoveAsync)  methode voor wachtrijen en [MemoryStoreSortedMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#RemoveAsync)  voor gesorteerde kaarten.

 |
| Interne Fout | |
-

Controleer de [Roblox statuspagina](https://status.roblox.com/pages/59db90dbcdeb2f04dadcf16d) .

-

Dien een [bugrapport](https://devforum.roblox.com/t/how-to-post-a-bug-report/24388)  in waarin je het probleem beschrijft met de Universum-ID van je game.

 |
| Ongeldige Aanvraag | |
-

Zorg ervoor dat je correcte en geldige parameters in je aanvraag opneemt. Voorbeelden van ongeldige parameters zijn:

-

Een lege string

-

Een string die de lengtelimiet overschrijdt

 |
| ItemValueSizeTooLarge | |
-

Shard of split de itemwaarde in meerdere sleutels.

-

Om gegroepeerde sleutels te organiseren, sorteer ze alfabetisch door een prefix  aan de sleutel toe te voegen.

-

Coderen of comprimeren van opgeslagen waarden.

 |

## [Testen en debuggen in Studio](#testen-en-debuggen-in-studio)[](#testen-en-debuggen-in-studio)

De gegevens in [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  zijn geïsoleerd tussen Studio en productie, zodat het wijzigen van de gegevens in Studio de productiegedragingen niet beïnvloedt. Dit betekent dat je API-aanroepen vanuit Studio geen toegang hebben tot productiedata, waardoor je geheugenopslag en nieuwe functies veilig kunt testen voordat je naar productie gaat.

Studio-testen hebben dezelfde [limieten en quotum](#limieten-en-quotum)  als productie. Voor quota die zijn berekend op basis van het aantal gebruikers, kan het resulterende quotum erg klein zijn, aangezien jij de enige gebruiker bent voor Studio-testen. Wanneer je vanuit Studio test, kun je ook iets hogere latentie en verhoogde foutpercentages opmerken in vergelijking met gebruik in productie vanwege enkele extra controles die worden uitgevoerd om toegang en machtigingen te verifiëren.

Voor informatie over hoe je een geheugenopslag in live games of tijdens het testen in de studio kunt debuggen, gebruik je de [Developer Console](/docs/nl-nl/studio/developer-console) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
