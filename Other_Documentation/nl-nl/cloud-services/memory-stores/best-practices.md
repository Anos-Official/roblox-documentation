<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/memory-stores/best-practices -->

Beste praktijken voor geheugenopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)

# Beste praktijken voor geheugenopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gebruik deze praktijken om tijdelijke gegevens te organiseren, de belasting te verdelen en te reageren op problemen met geheugenopslag.

Afhankelijk van het type gegevensstructuur, handhaaft [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  [limieten](/docs/nl-nl/cloud-services/memory-stores#limieten-voor-de-grootte-van-gegevensstructuren)  op het geheugen en het aantal items in een gegevensstructuur. Alle gegevensstructuren zijn ook beperkt door een globale per-partitie aanvraaglimiet.

## [Ontwerp sleutels en gegevensstructuren](#ontwerp-sleutels-en-gegevensstructuren)[](#ontwerp-sleutels-en-gegevensstructuren)

Zie [Gebruik statische sleutelpatronen en voorvoegsels](/docs/nl-nl/cloud-services/data-stores/best-practices#gebruik-statische-sleutelpatronen-en--voorvoegsels)  in [Beste praktijken voor gegevensopslag](/docs/nl-nl/cloud-services/data-stores/best-practices) . Pas die patronen toe op zowel sleutels als namen van gegevensstructuren, zodat elke server dezelfde logische gegevens naar dezelfde locatie leidt.

Kies vervaltijden die overeenkomen met hoe lang de gegevens nuttig blijven. Gebruik geen geheugenopslag voor persistente spelersrecords of gegevens die de vervaldatum moeten overleven. Voor hulp bij het kiezen tussen diensten, zie [Gegevensopslag versus geheugenopslag](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores) .

## [Omgaan met aanvraagfouten](#omgaan-met-aanvraagfouten)[](#omgaan-met-aanvraagfouten)

Zie [Herhaal tijdelijke fouten](/docs/nl-nl/cloud-services/data-stores/best-practices#herhaal-tijdelijke-fouten)  in [Beste praktijken voor gegevensopslag](/docs/nl-nl/cloud-services/data-stores/best-practices) .

## [Geef de voorkeur aan UpdateAsync boven SetAsync](#geef-de-voorkeur-aan-updateasync-boven-setasync)[](#geef-de-voorkeur-aan-updateasync-boven-setasync)

Zie [Geef de voorkeur aan UpdateAsync boven SetAsync](/docs/nl-nl/cloud-services/data-stores/best-practices#geef-de-voorkeur-aan-updateasync-boven-setasync)  in [Beste praktijken voor gegevensopslag](/docs/nl-nl/cloud-services/data-stores/best-practices) . Hash-maps en gesorteerde maps bieden [MemoryStoreHashMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  en [MemoryStoreSortedMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync)  voor dit patroon.

## [Verspreid terugkerende aanvragen](#verspreid-terugkerende-aanvragen)[](#verspreid-terugkerende-aanvragen)

Zie [Verspreid terugkerende aanvragen](/docs/nl-nl/cloud-services/data-stores/best-practices#verspreid-terugkerende-verzoeken)  in [Beste praktijken voor gegevensopslag](/docs/nl-nl/cloud-services/data-stores/best-practices) .

## [Monitor gebruik](#monitor-gebruik)[](#monitor-gebruik)

Gebruik het [Geheugenopslag Observability Dashboard](/docs/nl-nl/cloud-services/memory-stores/observability)  om het gebruik van quota, aanvraagvolume en responsstatussen te monitoren. Bekijk de ingebouwde e-mailmeldingen, configureer [aangepaste meldingen](/docs/nl-nl/production/analytics/alerts)  voor belangrijke statistieken van geheugenopslag en gebruik het [Foutrapport](/docs/nl-nl/production/analytics/error-report)  om fouten te onderzoeken.

Verminder aanvragen, itemgroottes en vervaltijden voordat je de capaciteit verhoogt. Als legitiem gebruik de standaardquota overschrijdt, evalueer dan [Uitgebreide Diensten](/docs/nl-nl/cloud-services/extended-services) .

## [Beheer limieten van gesorteerde kaarten en wachtrijen](#beheer-limieten-van-gesorteerde-kaarten-en-wachtrijen)[](#beheer-limieten-van-gesorteerde-kaarten-en-wachtrijen)

Gesorteerde kaarten en wachtrijen hebben beide limieten op het maximale aantal items en het maximale totale geheugen. Bovendien bevinden de items in een van deze gegevensstructuren zich altijd op een enkele partitie. Elke aanvraag aan een van die gegevensstructuren is een aanvraag aan dezelfde partitie.

Wanneer een gesorteerde kaart of wachtrij zijn item- of geheugengrens bereikt, verwijder dan onnodige items handmatig of door een vervalbeleid toe te voegen. Als alleen de geheugengrens throttling veroorzaakt, verminder dan de itemgroottes door onnodige informatie uit sleutels en waarden te verwijderen.

Als je al je items nodig hebt of throttling ervaart door aanvraagdoorvoer, is de enige oplossing sharding.

## [Verdeel de belasting met sharding](#verdeel-de-belasting-met-sharding)[](#verdeel-de-belasting-met-sharding)

Sharding is het proces van het opslaan van een set gerelateerde gegevens over meerdere gegevensstructuren. Met andere woorden, het betekent dat je een bestaande, hoogdoorvoerende gegevensstructuur vervangt door meerdere, kleinere structuren die samen dezelfde set gegevens bevatten als het origineel.

De belangrijkste uitdaging bij sharding is het vinden van een manier om de gegevens over meerdere gegevensstructuren te verspreiden op een manier die dezelfde functionaliteit behoudt als het origineel.

Hoewel Roblox al hash-maps partitioneert, kun je ze verder sharden door aanvragen over verschillende sleutels te verspreiden.

### [Sharding van een gesorteerde kaart](#sharding-van-een-gesorteerde-kaart)[](#sharding-van-een-gesorteerde-kaart)

Om spelersrecords in een gesorteerde kaart te sharden, gebruik je modulo-aritmetiek om elke [Id](/docs/nl-nl/reference/engine/datatypes/User#Id)  aan een van een vast aantal kaarten toe te wijzen. Het volgende voorbeeld gebruikt vier kaarten en leidt consequent dezelfde gebruiker naar dezelfde kaart:

Gebruik een hulpfunctie om de juiste gesorteerde kaart van een item sleutel te krijgen. Op deze manier hoef je niet hetzelfde codeblok voor elke functieaanroep te herhalen.

Sharding van een Gesorteerde Kaart

```

-- Initialiseer de MemoryStore Service

local MemoryStoreService = game:GetService("MemoryStoreService")

-- Maak je Gesorteerde Kaart emmers

local sm1 = MemoryStoreService:GetSortedMap("sm1")

local sm2 = MemoryStoreService:GetSortedMap("sm2")

local sm3 = MemoryStoreService:GetSortedMap("sm3")

local sm4 = MemoryStoreService:GetSortedMap("sm4")

local sortedMaps = { sm1, sm2, sm3, sm4 }

-- Hulpfunctie om de juiste emmer van de Item Sleutel op te halen

local function getSortedMapBucket(userId)

	local bucketIndex = (userId % #sortedMaps) + 1

	return sortedMaps[bucketIndex]

end

-- Initialiseer spelers met standaardwaarde van 0

for _, player in game:GetService("Players"):GetPlayers() do

	local userId = player.User.Id

	local bucket = getSortedMapBucket(userId)

	bucket:SetAsync(tostring(userId), 0, 600)

end

-- Haal de waarde van een speler op

local player = game:GetService("Players"):GetPlayers()[1]

local userId = player.User.Id

local bucket = getSortedMapBucket(userId)

local playerScore = bucket:GetAsync(tostring(userId))

print(playerScore)

```

### [Sharding van een wachtrij](#sharding-van-een-wachtrij)[](#sharding-van-een-wachtrij)

Sharding van een wachtrij is lastiger dan sharding van een gesorteerde kaart. Hoewel je de aanvraagdoorvoer over meerdere wachtrijen wilt verspreiden, vinden toevoegingen, lezingen en verwijderingen alleen plaats aan de voorkant of achterkant van de wachtrij.

Een oplossing is om een roterende wachtrij te gebruiken, wat betekent dat je meerdere wachtrijen maakt en tussen hen roteert wanneer je een item toevoegt of leest:

1.

Maak verschillende wachtrijen en voeg ze toe aan een array.

2.

Maak twee lokale pointers. De ene vertegenwoordigt de wachtrij waarvan je items wilt lezen en verwijderen. De andere vertegenwoordigt de wachtrij waaraan je items wilt toevoegen:

-

Voor leesbewerkingen, bereken het aantal items dat je uit elke wachtrij nodig hebt, evenals waar je de leespointer naartoe moet verplaatsen.

-

Voor verwijderbewerkingen, geef de ID's van de gelezen items door aan elke wachtrij.

-

Voor toevoegbewerkingen, voeg toe aan de wachtrij op de toevoegpointer en verhoog de pointer.

Sharding van een Wachtrij

```

-- Initialiseer de MemoryStore Service

local MemoryStoreService = game:GetService("MemoryStoreService")

-- Maak je Wachtrijen

local q1 = MemoryStoreService:GetQueue("q1")

local q2 = MemoryStoreService:GetQueue("q2")

local q3 = MemoryStoreService:GetQueue("q3")

local q4 = MemoryStoreService:GetQueue("q4")

-- Plaats de Wachtrijen in een Array

local queueArr = { q1, q2, q3, q4 }

-- Maak twee pointers die de indices van de lees- en toevoegwachtrijen vertegenwoordigen

local readIndex = 1

local addIndex = 1

-- Maak een lokale functie die de indices op de juiste manier bijwerkt

local function rotateIndex(index, n)

	return (index + n - 1) % 4 + 1

end

-- Maak een lokale functie die n items uit de wachtrij leest

local function readFromQueue(count, allOrNothing, waitTimeout)

	local endIndex = count % 4

	local countPerQueue = count // 4

	local items = {}

	local ids = {}

	-- loop door elke wachtrij

	for i = 1, 4, 1 do

		-- bepaal of deze wachtrij een extra item zal lezen

		local diff = i - readIndex

		if diff < 0 then

			diff += 4

		end

		local queue = queueArr[i]

		-- lees items uit elke wachtrij

		-- +1 items als het voldoet aan de extra leescriteria

		if diff < endIndex then

			items[i], ids[i] = queue:ReadAsync(countPerQueue + 1, allOrNothing, waitTimeout)

		else

			items[i], ids[i] = queue:ReadAsync(countPerQueue, allOrNothing, waitTimeout)

		end

	end

	readIndex = rotateIndex(readIndex, count)

	return items, ids

end

-- Maak een lokale functie die n items uit de wachtrij verwijdert

local function removeFromQueue(ids)

	for i = 1, 4, 1 do

		local queue = queueArr[i]

		queue:RemoveAsync(ids[i])

	end

end

-- Maak een lokale functie die een item aan de wachtrij toevoegt

local function addToQueue(itemKey, expiration, priority)

	local queue = queueArr[addIndex]

	queue:AddAsync(itemKey, expiration, priority)

	addIndex = rotateIndex(addIndex, 1)

end

-- Schrijf wat code!

for _, player in game:GetService("Players"):GetPlayers() do

	addToQueue(player.User.Id, 600, 0)

end

local players, ids = readFromQueue(20, true, -1)

removeFromQueue(ids)

```

### [Hash-maps](#hash-maps)[](#hash-maps)

Hash-maps hebben geen individuele geheugengrenzen of itemtellen en zijn automatisch geshard, maar je kunt nog steeds throttling tegenkomen als je ze slecht gebruikt.

Overweeg bijvoorbeeld een spel met een hash-map van gegevens, opgeslagen als de waarde van een enkele sleutel genaamd metadata . Als deze metadata een genest object bevat met informatie zoals plaats-ID, aantal spelers, en meer, moet je elke keer dat de metadata nodig is, GetAsync("metadata")  aanroepen en het hele object ophalen. In dit geval gaan alle aanvragen naar een enkele sleutel en dus naar een enkele partitie.

In plaats van alle metadata als een enkel, genest object op te slaan, sla je elk onafhankelijk benaderd veld op als zijn eigen sleutel, zodat de hash-map kan profiteren van automatische sharding. Als je scheiding nodig hebt tussen metadata en de rest van de hash-map, voeg dan een naamgevend voorvoegsel toe, zoals metadata_user_count  in plaats van user_count .

Als een of enkele sleutels frequente aanvragen ontvangen, shard die oproepen over meerdere sleutels. Als bijvoorbeeld alle spelservers een waarde van één hash-map sleutel ophalen, kunnen de aanvragen partition throttling veroorzaken. Om de belasting te verminderen, kopieer je de waarde naar meerdere sleutels en leid je elke server naar een stabiele shard.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
