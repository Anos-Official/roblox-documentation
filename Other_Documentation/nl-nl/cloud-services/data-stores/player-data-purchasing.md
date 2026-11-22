<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores/player-data-purchasing -->

Implementeer spelersdata en aankoopsystemen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Implementeer spelersdata en aankoopsystemen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

## [Achtergrond](#achtergrond)[](#achtergrond)

Roblox biedt een set API's om te communiceren met datastores via [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) . De meest voorkomende gebruikssituatie voor deze API's is het opslaan, laden en repliceren van * spelersdata* . Dat wil zeggen, data die is gekoppeld aan de voortgang van de speler, aankopen en andere sessiekenmerken die tussen individuele speelsessies behouden blijven.

De meeste spellen op Roblox gebruiken deze API's om een vorm van een spelersdatasysteem te implementeren. Deze implementaties verschillen in hun aanpak, maar proberen over het algemeen dezelfde set problemen op te lossen.

## [Veelvoorkomende problemen](#veelvoorkomende-problemen)[](#veelvoorkomende-problemen)

Hieronder staan enkele van de meest voorkomende problemen die spelersdatasystemen proberen op te lossen:

-

In Geheugen Toegang:  [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) -verzoeken maken webverzoeken die asynchroon werken en onderhevig zijn aan snelheidslimieten. Dit is geschikt voor een initiële laad bij het begin van de sessie, maar niet voor veelvuldige lees- en schrijfoperaties tijdens het normale spelverloop. De meeste spelersdatasystemen van ontwikkelaars slaan deze data in het geheugen op de Roblox-server op, waardoor [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) -verzoeken beperkt blijven tot de volgende scenario's:

-

Initiële lezing aan het begin van een sessie

-

Laatste schrijfoperatie aan het einde van de sessie

-

Periodieke schrijfbewerkingen op een interval om het scenario te mitigeren waarin de laatste schrijfoperatie mislukt

-

Schrijfbewerkingen om ervoor te zorgen dat data wordt opgeslagen tijdens het verwerken van een aankoop

-

Efficiënte Opslag:  Het opslaan van alle sessiedata van een speler in één tabel stelt je in staat om meerdere waarden atomair bij te werken en dezelfde hoeveelheid data in minder verzoeken te verwerken. Het verwijdert ook het risico van inter-waarde desynchronisatie en maakt terugdraaien gemakkelijker te begrijpen.

Sommige ontwikkelaars implementeren ook aangepaste serialisatie om grote datastructuren te comprimeren (typisch om in-game door gebruikers gegenereerde content op te slaan).

-

Replicatie:  De client heeft regelmatig toegang nodig tot de data van een speler (bijvoorbeeld om de UI bij te werken). Een generieke aanpak voor het repliceren van spelersdata naar de client stelt je in staat om deze informatie te verzenden zonder dat je op maat gemaakte replicatiesystemen voor elk datacomponent hoeft te maken. Ontwikkelaars willen vaak de optie om selectief te zijn over wat wel en niet naar de client wordt gerepliceerd.

-

Foutafhandeling:  Wanneer DataStores niet toegankelijk zijn, implementeren de meeste oplossingen een retry-mechanisme en een fallback naar 'standaard' data. Bijzondere zorg is nodig om ervoor te zorgen dat fallback-data later geen 'echte' data overschrijft, en dat dit op de juiste manier aan de speler wordt gecommuniceerd.

-

Retries:  Wanneer datastores niet toegankelijk zijn, implementeren de meeste oplossingen een retry-mechanisme en een fallback naar standaarddata. Neem bijzondere zorg om ervoor te zorgen dat fallback-data later geen "echte" data overschrijft, en communiceer de situatie op de juiste manier aan de speler.

-

Sessie Locking:  Als de data van een enkele speler op meerdere servers is geladen en in het geheugen is, kunnen er problemen optreden waarbij één server verouderde informatie opslaat. Dit kan leiden tot dataverlies en veelvoorkomende itemduplicatielussen.

-

Atomische Aankoopverwerking:  Verifieer, beloon en registreer aankopen atomair om te voorkomen dat items verloren gaan of meerdere keren worden toegekend.

## [Voorbeeldcode](#voorbeeldcode)[](#voorbeeldcode)

Deze code is alleen ter referentie en heeft zich niet bewezen over een lange periode in een populair spel. Het bestaat zodat je de aanpak kunt onderzoeken voor het oplossen van verschillende problemen en deze kunt toepassen op je eigen spelersdatasystemen. Gebruik deze code niet in je spel zoals het is zonder uitgebreide tests.

Roblox heeft referentiecode om je te helpen bij het ontwerpen en bouwen van spelersdatasystemen. De rest van deze pagina behandelt achtergrond, implementatiedetails en algemene kanttekeningen.

 [Krijg de Code](https://create.roblox.com/store/asset/14376223840/Purchase-Handling))

Nadat je het model in Studio hebt geïmporteerd, zou je de volgende mappenstructuur moeten zien:

 ![Explorer-venster dat het aankoopsysteemmodel toont.](https://prod.docsiteassets.roblox.com/assets/data/player-data-purchasing/Sample-Hierarchy.png)

## [Architectuur](#architectuur)[](#architectuur)

Dit diagram op hoog niveau illustreert de belangrijkste systemen in het voorbeeld en hoe ze interfacing met code in de rest van het spel.

 ![Een architectuurdiagram voor de voorbeeldcode.](https://prod.docsiteassets.roblox.com/assets/data/player-data-purchasing/sample-architecture.png)

## [Retries](#retries)[](#retries)

Class:  [DataStoreWrapper](#voorbeeldcode)

### [Achtergrond](#achtergrond-1)[](#achtergrond-1)

Aangezien [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  webverzoeken onder de motorkap maakt, is het niet gegarandeerd dat deze verzoeken slagen. Wanneer dit gebeurt, werpen de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) -methoden fouten, waardoor je ze kunt afhandelen.

Een veelvoorkomende "valstrik" kan optreden als je probeert om fouten in de datastore op deze manier af te handelen:

```

local MAX_ATTEMPTS = 5

local BASE_DELAY = 2

local MAX_DELAY = 32

local function retrySetAsync(dataStore, key, value)

	for attempt = 1, MAX_ATTEMPTS do

		local success, result = pcall(dataStore.SetAsync, dataStore, key, value)

		if success then

			return result

		end

		if attempt < MAX_ATTEMPTS then

			local backoff = math.min(MAX_DELAY, BASE_DELAY * (2 ^ (attempt - 1)))

			local jitter = math.random() * backoff

			task.wait(math.min(MAX_DELAY, backoff + jitter))

		end

	end

end

```

Herhaal tijdelijke fouten met exponentiële backoff en willekeurige jitter zodat servers niet gelijktijdig opnieuw proberen. Beperk de vertraging en het aantal pogingen.

Zelfs met dat vertragingpatroon is dit retry-mechanisme niet geschikt voor [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) -verzoeken omdat het de volgorde waarin verzoeken worden gedaan niet garandeert. Het behouden van de volgorde van verzoeken is belangrijk voor [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) -verzoeken omdat ze interageren met de status. Overweeg het volgende scenario:

1.

Verzoek A wordt gedaan om de waarde van sleutel K  op 1 in te stellen.

2.

Het verzoek mislukt, dus een retry wordt gepland om na de backoff-vertraging te worden uitgevoerd.

3.

Voordat de retry plaatsvindt, stelt verzoek B de waarde van K  in op 2, maar de retry van verzoek A overschrijft deze waarde onmiddellijk en stelt K  in op 1.

Zelfs als [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  op de laatste versie van de waarde van de sleutel werkt, moeten [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) -verzoeken nog steeds in volgorde worden verwerkt om ongeldige tijdelijke staten te voorkomen (bijvoorbeeld, een aankoop trekt munten af voordat een munttoename wordt verwerkt, wat resulteert in negatieve munten).

Ons spelersdatasysteem gebruikt een nieuwe klasse, DataStoreWrapper , die yieldende retries biedt die gegarandeerd in volgorde per sleutel worden verwerkt.

### [Aanpak](#aanpak)[](#aanpak)

 ![Een procesdiagram dat het retry-systeem illustreert](https://prod.docsiteassets.roblox.com/assets/data/player-data-purchasing/retry-diagram.png)

DataStoreWrapper  biedt methoden die overeenkomen met de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) -methoden: [DataStore:GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync) , [DataStore:SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync) , [DataStore:UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  en [DataStore:RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync) .

Deze methoden, wanneer ze worden aangeroepen:

1.

Voeg het verzoek toe aan een wachtrij. Elke sleutel heeft zijn eigen wachtrij, waar verzoeken in volgorde en in serie worden verwerkt. De aanroepende thread yieldt totdat het verzoek is voltooid.

Deze functionaliteit is gebaseerd op de ThreadQueue -klasse, die een coroutine-gebaseerde taakplanner en snelheidsbegrenzer is. In plaats van een belofte terug te geven, yieldt ThreadQueue  de huidige thread totdat de bewerking is voltooid en gooit een fout als deze mislukt. Dit is consistenter met idiomatische asynchrone Luau-patronen.

2.

Als een verzoek mislukt, probeert het opnieuw met een configureerbare exponentiële backoff. Deze retries maken deel uit van de callback die aan de ThreadQueue  is ingediend, zodat ze gegarandeerd worden voltooid voordat het volgende verzoek in de wachtrij voor deze sleutel begint.

3.

Wanneer een verzoek is voltooid, retourneert de verzoekmethode met het success, result -patroon.

DataStoreWrapper  biedt ook methoden om de wachtrijlengte voor een gegeven sleutel op te vragen en verouderde verzoeken te wissen. De laatste optie is bijzonder nuttig in scenario's waarin de server wordt afgesloten en er geen tijd is om andere dan de meest recente verzoeken te verwerken.

### [Kanttekeningen](#kanttekeningen)[](#kanttekeningen)

DataStoreWrapper  volgt het principe dat, buiten extreme scenario's, elk datastoreverzoek moet worden toegestaan om te voltooien (succesvol of anderszins), zelfs als een recenter verzoek het overbodig maakt. Wanneer een nieuw verzoek plaatsvindt, worden verouderde verzoeken niet uit de wachtrij verwijderd, maar mogen ze in plaats daarvan worden voltooid voordat het nieuwe verzoek wordt gestart. De reden hiervoor is geworteld in de toepasbaarheid van deze module als een generieke datastore-hulpmiddel in plaats van een specifiek hulpmiddel voor spelersdata, en is als volgt:

1.

Het is moeilijk om een intuïtieve set regels te bepalen voor wanneer een verzoek veilig kan worden verwijderd uit de wachtrij. Overweeg de volgende wachtrij:

Value=0, SetAsync(1), GetAsync(), SetAsync(2)

Het verwachte gedrag is dat [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  1  zou retourneren, maar als we het [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync) -verzoek uit de wachtrij verwijderen omdat het overbodig is gemaakt door het meest recente, zou het 0  retourneren.

De logische voortgang is dat wanneer een nieuw schrijfverzoek wordt toegevoegd, alleen verouderde verzoeken tot aan het meest recente leesverzoek moeten worden verwijderd. [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) , veruit de meest voorkomende bewerking (en de enige die door dit systeem wordt gebruikt), kan zowel lezen als schrijven, dus het zou moeilijk zijn om dit binnen dit ontwerp te verzoenen zonder extra complexiteit toe te voegen.

DataStoreWrapper  zou vereisen dat je opgeeft of een [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) -verzoek was toegestaan om te lezen en/of te schrijven, maar het zou geen toepasbaarheid hebben voor ons spelersdatasysteem, waar dit niet van tevoren kan worden bepaald vanwege het sessielockmechanisme (later in meer detail behandeld).

2.

Zodra ze uit de wachtrij zijn verwijderd, is het moeilijk om een intuïtieve regel te bepalen voor * hoe*  dit moet worden afgehandeld. Wanneer een DataStoreWrapper -verzoek wordt gedaan, wordt de huidige thread yield totdat het is voltooid. Als we verouderde verzoeken uit de wachtrij zouden verwijderen, zouden we moeten beslissen of we false, "Verwijderd uit wachtrij"  of nooit retourneren en de actieve thread weggooien. Beide benaderingen hebben hun eigen nadelen en leggen extra complexiteit op de consument.

Uiteindelijk is onze mening dat de eenvoudige aanpak (elke aanvraag verwerken) hier de voorkeur heeft en een duidelijkere omgeving creëert om te navigeren bij het benaderen van complexe problemen zoals sessielocking. De enige uitzondering hierop is tijdens [DataModel:BindToClose()](/docs/nl-nl/reference/engine/classes/DataModel#BindToClose) , waar het wissen van de wachtrij noodzakelijk wordt om de data van alle gebruikers op tijd op te slaan en de waarde die individuele functieaanroepen retourneren geen voortdurende zorg meer is. Om hier rekening mee te houden, bieden we een skipAllQueuesToLastEnqueued -methode aan. Voor meer context, zie [Spelersdata](#spelersdata) .

## [Sessie Locking](#sessie-locking)[](#sessie-locking)

Class:  [SessionLockedDataStoreWrapper](#voorbeeldcode)

### [Achtergrond](#achtergrond-2)[](#achtergrond-2)

Spelersdata wordt in het geheugen op de server opgeslagen en wordt alleen gelezen en geschreven naar de onderliggende datastores wanneer dat nodig is. Je kunt in-memory spelersdata onmiddellijk lezen en bijwerken zonder webverzoeken en voorkomen dat je de limieten van [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  overschrijdt.

Voor dit model om te werken zoals bedoeld, is het van cruciaal belang dat niet meer dan één server in staat is om de data van een speler tegelijkertijd in het geheugen te laden vanuit de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) .

Bijvoorbeeld, als server A de data van een speler laadt, kan server B die data niet laden totdat server A zijn lock op die data vrijgeeft tijdens een laatste opslaan. Zonder een lockmechanisme zou server B verouderde spelersdata uit de datastore kunnen laden voordat server A de kans heeft om de recentere versie die het in het geheugen heeft op te slaan. Dan, als server A zijn nieuwere data opslaat nadat server B de verouderde data heeft geladen, zou server B die nieuwere data overschrijven tijdens zijn volgende opslaan.

Hoewel Roblox alleen toestaat dat een client met één server tegelijk is verbonden, kun je niet aannemen dat data van de ene sessie altijd is opgeslagen voordat de volgende sessie begint. Overweeg de volgende scenario's die kunnen optreden wanneer een speler server A verlaat:

1.

Server A doet een [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) -verzoek om hun data op te slaan, maar het verzoek mislukt en vereist verschillende retries om succesvol te voltooien. Tijdens de retry-periode voegt de speler zich bij server B.

2.

Server A doet te veel [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) -aanroepen naar dezelfde sleutel en wordt vertraagd. Het laatste opslaan wordt in een wachtrij geplaatst. Terwijl het verzoek in de wachtrij staat, voegt de speler zich bij server B.

3.

Op server A yieldt een stuk code dat is verbonden met het [PlayerRemoving](/docs/nl-nl/reference/engine/classes/Players#PlayerRemoving) -evenement voordat de data van de speler is opgeslagen. Voordat deze bewerking is voltooid, voegt de speler zich bij server B.

4.

De prestaties van server A zijn zo verslechterd dat het laatste opslaan wordt vertraagd totdat de speler zich bij server B voegt.

Deze scenario's zouden zeldzaam moeten zijn, maar ze komen voor, vooral in situaties waarin een speler snel achtereenvolgens van de ene server naar de andere schakelt (bijvoorbeeld tijdens teleportatie). Sommige kwaadwillende gebruikers kunnen zelfs proberen dit gedrag te misbruiken om acties te voltooien zonder dat ze persistent zijn. Dit kan bijzonder impactvol zijn in spellen die spelers toestaan om te handelen en is een veelvoorkomende bron van exploits voor itemduplicatie.

Sessie locking pakt deze kwetsbaarheid aan door ervoor te zorgen dat wanneer de sleutel van een speler voor het eerst door de server wordt gelezen, de server atomisch een lock naar de metadata van de sleutel schrijft binnen dezelfde [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) -aanroep. Als deze lockwaarde aanwezig is wanneer een andere server probeert de sleutel te lezen of te schrijven, gaat de server niet verder.

### [Aanpak](#aanpak-1)[](#aanpak-1)

 ![Een procesdiagram dat het sessielocksysteem illustreert](https://prod.docsiteassets.roblox.com/assets/data/player-data-purchasing/session-lock-diagram.png)

SessionLockedDataStoreWrapper  is een meta-wrapper rond de DataStoreWrapper -klasse. DataStoreWrapper  biedt wachtrij- en retry-functionaliteit, die SessionLockedDataStoreWrapper  aanvult met sessielocking.

SessionLockedDataStoreWrapper  laat elk [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) -verzoek—ongeacht of het [GetAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync) , [SetAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  of [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  is—door [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) . Dit komt omdat [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  het mogelijk maakt om een sleutel atomisch te lezen en te schrijven. Het is ook mogelijk om de schrijfoperatie te verlaten op basis van de gelezen waarde door nil  in de transformatiecallback terug te geven.

De transformatiefunctie die in [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  voor elk verzoek wordt doorgegeven, voert de volgende bewerkingen uit:

1.

Verifieert of de sleutel veilig is om te benaderen, en verlaat de bewerking als dat niet het geval is. "Veilig om te benaderen" betekent:

-

Het metadata-object van de sleutel bevat geen onherkenbare LockId -waarde die minder dan de lockvervaltijd geleden voor het laatst is bijgewerkt. Dit houdt rekening met het respecteren van een lock die door een andere server is geplaatst en met het negeren van die lock als deze is verlopen.

-

Als deze server eerder zijn eigen LockId -waarde in de metadata van de sleutel heeft geplaatst, dan is deze waarde nog steeds in de metadata van de sleutel. Dit houdt rekening met de situatie waarin een andere server de lock van deze server heeft overgenomen (door verval of door dwang) en deze later heeft vrijgegeven. Alternatief geformuleerd, zelfs als LockId  nil  is, zou een andere server nog steeds een lock kunnen hebben vervangen en verwijderd in de tijd sinds je de sleutel hebt vergrendeld.

2.

[UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  voert de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) -bewerking uit die de consument van SessionLockedDataStoreWrapper  heeft aangevraagd. Bijvoorbeeld, [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  vertaalt naar function(value) return value end .

3.

Afhankelijk van de parameters die in het verzoek zijn doorgegeven, vergrendelt of ontgrendelt [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  de sleutel:

1.

Als de sleutel moet worden vergrendeld, stelt [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  de LockId  in de metadata van de sleutel in op een GUID. Deze GUID wordt in het geheugen op de server opgeslagen, zodat deze de volgende keer dat deze de sleutel benadert kan worden geverifieerd. Als de server al een lock op deze sleutel heeft, worden er geen wijzigingen aangebracht. Het plant ook een taak om je te waarschuwen als je de sleutel niet opnieuw benadert om de lock binnen de vervaltijd van de lock te behouden.

2.

Als de sleutel moet worden ontgrendeld, verwijdert [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  de LockId  in de metadata van de sleutel.

Een aangepaste retry-handler wordt doorgegeven aan de onderliggende DataStoreWrapper , zodat de bewerking opnieuw wordt geprobeerd als deze is afgebroken in stap 1 vanwege de sessie die vergrendeld is.

Een aangepaste foutmelding wordt ook teruggegeven aan de consument, zodat het spelersdatasysteem een alternatieve fout kan rapporteren in het geval van sessielocking aan de client.

### [Kanttekeningen](#kanttekeningen-1)[](#kanttekeningen-1)

Het sessielockregime is afhankelijk van een server die altijd zijn lock op een sleutel vrijgeeft wanneer deze klaar is met het gebruik ervan. Dit zou altijd moeten gebeuren via een instructie om de sleutel te ontgrendelen als onderdeel van de laatste schrijfoperatie in [PlayerRemoving](/docs/nl-nl/reference/engine/classes/Players#PlayerRemoving)  of [BindToClose()](/docs/nl-nl/reference/engine/classes/DataModel#BindToClose) .

Echter, de ontgrendeling kan in bepaalde situaties mislukken. Bijvoorbeeld:

-

De server is gecrasht of [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  was onbruikbaar voor alle pogingen om de sleutel te benaderen.

-

Vanwege een fout in de logica of een soortgelijke bug is de instructie om de sleutel te ontgrendelen niet gegeven.

Om de lock op een sleutel te behouden, moet je deze regelmatig benaderen zolang deze in het geheugen is geladen. Dit zou normaal gesproken worden gedaan als onderdeel van de auto-save-loop die op de achtergrond draait in de meeste spelersdatasystemen, maar dit systeem biedt ook een refreshLockAsync -methode als je het handmatig moet doen.

Als de vervaltijd van de lock is overschreden zonder dat de lock is bijgewerkt, is elke server vrij om de lock over te nemen. Als een andere server de lock overneemt, mislukken pogingen van de huidige server om de sleutel te lezen of te schrijven, tenzij deze een nieuwe lock vestigt.

## [Verwerking van ontwikkelaarsproducten](#verwerking-van-ontwikkelaarsproducten)[](#verwerking-van-ontwikkelaarsproducten)

Singleton:  [ReceiptHandler](#voorbeeldcode)

### [Achtergrond](#achtergrond-3)[](#achtergrond-3)

De ProcessReceipt -callback vervult de cruciale taak om te bepalen wanneer een aankoop moet worden afgerond. ProcessReceipt  wordt in zeer specifieke scenario's aangeroepen. Voor de garanties ervan, zie [MarketplaceService.ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt) .

Hoewel de definitie van "afhandelen" van een aankoop kan verschillen tussen spellen, gebruiken we de volgende criteria:

1.

De aankoop is nog niet eerder afgehandeld.

2.

De aankoop wordt weerspiegeld in de huidige sessie.

3.

De aankoop is opgeslagen in de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) .

Elke aankoop, zelfs eenmalige consumables, moet worden weerspiegeld in de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) , zodat de aankoopgeschiedenis van gebruikers is opgenomen in hun sessiedata.

Dit vereist het uitvoeren van de volgende bewerkingen voordat PurchaseGranted  wordt geretourneerd:

1.

Verifieer dat de PurchaseId  nog niet is geregistreerd als afgehandeld.

2.

Ken de aankoop toe in de in-memory spelersdata van de speler.

3.

Registreer de PurchaseId  als afgehandeld in de in-memory spelersdata van de speler.

4.

Schrijf de in-memory spelersdata van de speler naar de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) .

Sessie locking vereenvoudigt deze stroom, omdat je je geen zorgen meer hoeft te maken over de volgende scenario's:

-

De in-memory spelersdata op de huidige server die mogelijk verouderd is, waardoor je de laatste waarde uit de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore)  moet ophalen voordat je de PurchaseId -geschiedenis verifieert.

-

De callback voor dezelfde aankoop die op een andere server draait, waardoor je zowel de PurchaseId -geschiedenis moet lezen als schrijven en de bijgewerkte spelersdata met de aankoop atomair moet opslaan om racecondities te voorkomen.

Sessie locking garandeert dat, als een poging om naar de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore)  van de speler te schrijven succesvol is, geen enkele andere server succesvol de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore)  van de speler heeft gelezen of geschreven tussen het laden en opslaan van de data op deze server. Kortom, de in-memory spelersdata op deze server is de meest actuele versie die beschikbaar is. Er zijn enkele kanttekeningen, maar deze beïnvloeden dit gedrag niet.

### [Aanpak](#aanpak-2)[](#aanpak-2)

De opmerkingen in ReceiptProcessor  schetsen de aanpak:

1.

Verifieer dat de data van de speler momenteel op deze server is geladen en dat deze zonder fouten is geladen.

Omdat dit systeem sessielocking gebruikt, verifieert deze controle ook dat de in-memory data de meest actuele versie is.

Als de data van de speler nog niet is geladen (wat te verwachten is wanneer een speler zich bij een spel voegt), wacht dan tot de data van de speler is geladen. Het systeem luistert ook naar de speler die het spel verlaat voordat hun data is geladen, omdat het niet oneindig moet yielden en deze callback niet opnieuw moet blokkeren op deze server voor deze aankoop als de speler zich opnieuw voegt.

2.

Verifieer dat de PurchaseId  nog niet is geregistreerd als verwerkt in de spelersdata.

Vanwege sessielocking is de array van PurchaseIds  die het systeem in het geheugen heeft de meest actuele versie. Als de PurchaseId  is geregistreerd als verwerkt en wordt weerspiegeld in een waarde die is geladen of opgeslagen in de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) , retourneer dan PurchaseGranted . Als deze is geregistreerd als verwerkt, maar * niet*  wordt weerspiegeld in de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) , retourneer dan NotProcessedYet .

3.

Werk de spelersdata lokaal bij op deze server om de aankoop "toe te kennen".

ReceiptProcessor  neemt een generieke callback-aanpak en wijst een andere callback toe voor elke DeveloperProductId .

Zodra deze stap is voltooid, krijgt de speler toegang tot de aankoop in de huidige sessie. Dit betekent dat als de spelersdata in stap 5 niet kan worden opgeslagen, de speler de aankoop gratis ontvangt voor de duur van de sessie.

4.

Werk de spelersdata lokaal bij op deze server om de PurchaseId  op te slaan.

5.

Dien een verzoek in om de in-memory data op te slaan naar de [DataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore) , waarbij PurchaseGranted  wordt geretourneerd als het verzoek succesvol is. Zo niet, retourneer dan NotProcessedYet .

Als dit opslaan verzoek niet succesvol is, kan een later verzoek om de in-memory sessiedata van de speler nog steeds slagen. Tijdens de volgende ProcessReceipt -aanroep behandelt stap 2 deze situatie en retourneert PurchaseGranted .

## [Spelersdata](#spelersdata)[](#spelersdata)

Singletons:  [PlayerData.Server](#voorbeeldcode) , [PlayerData.Client](#voorbeeldcode)

### [Achtergrond](#achtergrond-4)[](#achtergrond-4)

Modules die een interface bieden voor code om synchronisch spelerssessiedata te lezen en te schrijven zijn gebruikelijk in Roblox-spellen. Deze sectie behandelt PlayerData.Server  en PlayerData.Client .

### [Aanpak](#aanpak-3)[](#aanpak-3)

PlayerData.Server  en PlayerData.Client  behandelen het volgende:

1.

Het laden van de data van de speler in het geheugen, inclusief het afhandelen van gevallen waarin het laden mislukt

2.

Het bieden van een interface voor servercode om de spelersdata op te vragen en te wijzigen

3.

Het repliceren van wijzigingen in de spelersdata naar de client, zodat clientcode er toegang toe heeft

4.

Het repliceren van laad- en/of opslaanfouten naar de client, zodat deze foutdialoogvensters kan tonen

5.

Het periodiek opslaan van de spelersdata, wanneer de speler vertrekt en wanneer de server wordt afgesloten

#### [Laad spelersdata](#laad-spelersdata)[](#laad-spelersdata)

 ![Een procesdiagram dat het laadsysteem illustreert](https://prod.docsiteassets.roblox.com/assets/data/player-data-purchasing/data-load-diagram.png)

1.

SessionLockedDataStoreWrapper  doet een getAsync -verzoek naar de datastore.

Als dit verzoek mislukt, wordt de standaarddata gebruikt en wordt het profiel gemarkeerd als "foutief" om ervoor te zorgen dat het later niet naar de datastore wordt geschreven.

Een alternatieve optie is om de speler te kickeren, maar we raden aan de speler met standaarddata te laten spelen en duidelijke berichten te geven over wat er is gebeurd in plaats van ze uit het spel te verwijderen.

2.

Een initiële payload wordt verzonden naar PlayerDataClient  met de geladen data en de foutstatus (indien aanwezig).

3.

Alle threads die zijn yield met waitForDataLoadAsync  voor de speler worden hervat.

#### [Bied een interface voor servercode](#bied-een-interface-voor-servercode)[](#bied-een-interface-voor-servercode)

-

PlayerDataServer  is een singleton die kan worden vereist en benaderd door elke servercode die in dezelfde omgeving draait.

-

Spelersdata is georganiseerd in een woordenboek van sleutels en waarden. Je kunt deze waarden op de server manipuleren met de methoden setValue , getValue , updateValue  en removeValue . Deze methoden werken allemaal synchronisch zonder te yielden.

-

De methoden hasLoaded  en waitForDataLoadAsync  zijn beschikbaar om ervoor te zorgen dat de data is geladen voordat je deze benadert. We raden aan dit eenmaal te doen tijdens een laadscherm voordat andere systemen worden gestart om te voorkomen dat je voor elke interactie met data op de client moet controleren op laadfouten.

-

Een hasErrored -methode kan opvragen of de initiële laad van de speler is mislukt, waardoor ze standaarddata gebruiken. Controleer deze methode voordat je de speler toestaat om aankopen te doen, aangezien aankopen niet naar data kunnen worden opgeslagen zonder een succesvolle laad.

-

Een playerDataUpdated -signaal wordt geactiveerd met de player , key  en value  telkens wanneer de data van een speler wordt gewijzigd. Individuele systemen kunnen zich hierop abonneren.

#### [Repliceer wijzigingen naar de client](#repliceer-wijzigingen-naar-de-client)[](#repliceer-wijzigingen-naar-de-client)

-

Elke wijziging in de spelersdata in PlayerDataServer  wordt gerepliceerd naar PlayerDataClient , tenzij die sleutel als privé is gemarkeerd met setValueAsPrivate

-

setValueAsPrivate  wordt gebruikt om sleutels aan te duiden die niet naar de client moeten worden verzonden

-

PlayerDataClient  bevat een methode om de waarde van een sleutel op te vragen (get) en een signaal dat wordt geactiveerd wanneer deze wordt bijgewerkt (updated). Een hasLoaded -methode en een loaded -signaal zijn ook inbegrepen, zodat de client kan wachten op het laden en repliceren van data voordat zijn systemen worden gestart

-

PlayerDataClient  is een singleton die kan worden vereist en benaderd door elke clientcode die in dezelfde omgeving draait

#### [Repliceer fouten naar de client](#repliceer-fouten-naar-de-client)[](#repliceer-fouten-naar-de-client)

-

Foutstatussen die worden ondervonden bij het opslaan of laden van spelersdata worden gerepliceerd naar PlayerDataClient .

-

Toegang tot deze informatie met de methoden getLoadError  en getSaveError , samen met de signalen loaded  en saved .

-

Er zijn twee soorten fouten: DataStoreError  (het [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) -verzoek is mislukt) en SessionLocked  (zie [Sessie Locking](#sessie-locking) ).

-

Gebruik deze gebeurtenissen om clientaankoopprompten uit te schakelen en waarschuwingsdialoogvensters te implementeren. Deze afbeelding toont een voorbeelddialoog:

 ![Een screenshot van een voorbeeldwaarschuwing die kan worden weergegeven wanneer spelersdata niet kan worden geladen](https://prod.docsiteassets.roblox.com/assets/data/player-data-purchasing/data-warning.png)

#### [Sla spelersdata op](#sla-spelersdata-op)[](#sla-spelersdata-op)

 ![Een procesdiagram dat het opslaan van het systeem illustreert](https://prod.docsiteassets.roblox.com/assets/data/player-data-purchasing/data-save-diagram.png)

1.

Wanneer de speler het spel verlaat, neemt het systeem de volgende stappen:

1.

Controleer of het veilig is om de spelersdata naar de datastore te schrijven. Scenario's waarin het onveilig zou zijn, zijn onder andere dat de spelersdata niet is geladen of nog steeds aan het laden is.

2.

Doe een verzoek via de SessionLockedDataStoreWrapper  om de huidige in-memory datavalue naar de datastore te schrijven en verwijder de sessielock zodra dit is voltooid.

3.

Wis de spelersdata (en andere variabelen zoals metadata en foutstatussen) uit het servergeheugen.

2.

In een periodieke loop schrijft de server de data van elke speler naar de datastore (op voorwaarde dat het veilig is om op te slaan). Deze welkomstredundantie vermindert verlies in het geval van een servercrash en is ook noodzakelijk om de sessielock te behouden.

Het voorbeeld start één gedeelde loop na AUTO_SAVE_INTERVAL  seconden (180 standaard) en slaat vervolgens elke geladen speler parallel op. Die loop offset niet servers of spelers, zodat servers die op vergelijkbare tijden starten samen kunnen flushen.

Offset de eerste opslag van elke speler met een willekeurige duur binnen het interval, zodat live servers niet allemaal op hetzelfde moment schrijven:

```

local AUTO_SAVE_INTERVAL = 180

local function startAutoSave(player)

	task.spawn(function()

		task.wait(math.random() * AUTO_SAVE_INTERVAL)

		while player.Parent do

			if canSave(player) then

				savePlayerData(player)

			end

			task.wait(AUTO_SAVE_INTERVAL)

		end

	end)

end

```

3.

Wanneer een verzoek om de server af te sluiten wordt ontvangen, gebeurt het volgende in een [BindToClose](/docs/nl-nl/reference/engine/classes/DataModel#BindToClose) -callback:

1.

Er wordt een verzoek gedaan om de data van elke speler op de server op te slaan, volgens het proces dat normaal wordt doorlopen wanneer een speler de server verlaat. Deze verzoeken worden parallel gedaan, aangezien [BindToClose](/docs/nl-nl/reference/engine/classes/DataModel#BindToClose) -callbacks slechts 30 seconden hebben om te voltooien.

2.

Om de opslagen te versnellen, worden alle andere verzoeken in de wachtrij van elke sleutel gewist uit de onderliggende DataStoreWrapper  (zie [Retries](#retries) ).

3.

De callback retourneert pas als alle verzoeken zijn voltooid.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
