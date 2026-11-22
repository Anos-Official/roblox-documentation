<!-- Source: https://create.roblox.com/docs/nl-nl/luau/queues -->

Wachtrijen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Gegevensstructuren

# Wachtrijen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een wachtrij is een lineaire datastructuur met een verzameling items. Er zijn twee soorten wachtrijen op Roblox: [gewone wachtrijen](#gewone-wachtrijen) , die het first-in-first-out (FIFO) principe volgen, en [prioriteitswachtrijen](#prioriteitswachtrijen) , die prioriteiten hebben voor items in de wachtrij die de volgorde van gegevenstoegang bepalen. Items in beide soorten wachtrijen kunnen elk Luau [gegevenstype](/docs/nl-nl/luau#typen)  zijn.

Wachtrij is een ingebouwde datastructuur van de [niet-permanente gegevensopslag](/docs/nl-nl/cloud-services/memory-stores/queue)  service genaamd [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService) , waarvoor je direct de ingebouwde functies kunt aanroepen om een wachtrij te krijgen en gegevens aan de wachtrij toe te voegen, te lezen of te verwijderen. Voor elk ander gebruik, zoals het plannen van taken en het afhandelen van verzoeken in je game, kun je tabellen gebruiken om zelf wachtrijen te implementeren.

## [Gewone wachtrijen](#gewone-wachtrijen)[](#gewone-wachtrijen)

Gewone wachtrijen worden onderhouden in de FIFO-volgorde, waarin alle items aan de achterkant van de wachtrij worden toegevoegd en in dezelfde volgorde worden gelezen of verwijderd als ze zijn toegevoegd, van de voorkant naar de achterkant.

![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Regular-Queue-Diagram.png) De volgorde waarin een gewone wachtrij items toevoegt, leest en verwijdert

## [Prioriteitswachtrijen](#prioriteitswachtrijen)[](#prioriteitswachtrijen)

Prioriteitswachtrijen volgen niet de FIFO-regel, waarin elk item kan worden toegevoegd met een prioriteitsnummer dat de volgorde aangeeft waarin het wordt gelezen of verwijderd. Het item aan de achterkant van een prioriteitswachtrij heeft de standaardprioriteit van 0, en het item aan de voorkant van de wachtrij heeft de hoogste ingestelde prioriteit, die 5 is in het volgende voorbeeld.

![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Priority-Queue-Diagram.png) De ingestelde prioriteit van een item verandert de volgorde waarin een wachtrij items leest

In dit voorbeeld wordt een item met een ingestelde prioriteit van 3 aan een wachtrij toegevoegd. De wachtrij plaatst het nieuwe item achter alle bestaande items met de ingestelde prioriteit van 3 of meer. Om een item aan de voorkant van de wachtrij te plaatsen, moet je de prioriteit hoger instellen dan de huidige hoogste ingestelde prioriteit. In dit voorbeeld moet je de prioriteit op 6 of hoger instellen.

Prioriteitswachtrijen zijn nuttig voor situaties waarin je gegevens wilt lezen of benaderen op basis van de volgorde van belangrijkheid in plaats van de volgorde van toevoeging. Je kunt een prioriteit instellen als een geheel getal bij het toevoegen van een item, en de wachtrij verwerkt items met een hogere prioriteit voordat items met lagere prioriteiten. Je kunt bijvoorbeeld prioriteitswachtrijen gebruiken voor matchmaking door hogere prioriteiten toe te wijzen aan gebruikers die al lange tijd wachten.

## [Wachtrijen implementeren](#wachtrijen-implementeren)[](#wachtrijen-implementeren)

Je kunt de ingebouwde wachtrijen van [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  gebruiken of [tabellen](/docs/nl-nl/luau/tables)  gebruiken om wachtrijen voor alle andere toepassingen te implementeren. Het volgende codevoorbeeld toont de implementatie van een gewone wachtrij . Om deze implementatie voor je game te gebruiken, moet je het opslaan als een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  en het in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  opslaan, zodat je wachtrij toegankelijk is voor zowel client als server.

Implementatie van een Gewone Wachtrij met Tabel

```

--!strict

local Queue = {}

Queue.__index = Queue

export type Queue<T> = typeof(setmetatable(

	{} :: {

		_first: number,

		_last: number,

		_queue: { T },

	},

	Queue

))

function Queue.new<T>(): Queue<T>

	local self = setmetatable({

		_first = 0,

		_last = -1,

		_queue = {},

	}, Queue)

	return self

end

-- Controleer of de wachtrij leeg is

function Queue.isEmpty<T>(self: Queue<T>)

	return self._first > self._last

end

-- Voeg een waarde toe aan de wachtrij

function Queue.enqueue<T>(self: Queue<T>, value: T)

	local last = self._last + 1

	self._last = last

	self._queue[last] = value

end

-- Verwijder een waarde uit de wachtrij

function Queue.dequeue<T>(self: Queue<T>): T

	if self:isEmpty() then

		error("Kan niet uit een lege wachtrij verwijderen")

	end

	local first = self._first

	local value = self._queue[first]

	self._queue[first] = nil

	self._first = first + 1

	return value

end

return Queue

```

Het volgende codevoorbeeld is een gebruiksvoorbeeld als een [Script](/docs/nl-nl/reference/engine/classes/Script)  onder [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . Je kunt de code, het type en de opslaglocatie aanpassen aan je eigen gebruik, zolang je de vorige implementatiecode correct hebt opgeslagen.

Voorbeeld van Gewone Wachtrij Gebruik

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Queue = require(ReplicatedStorage:WaitForChild("Queue"))

local myQueue = Queue.new()

-- Voeg enkele waarden toe aan de wachtrij

myQueue:enqueue(5)

myQueue:enqueue(10)

myQueue:enqueue(15)

-- myQueue = { 5, 10, 15 }

-- Verwijder een waarde uit de wachtrij

local first = myQueue:dequeue()

print("De eerste waarde die aan de wachtrij is toegevoegd was", first)

-- myQueue = { 10, 15 }

-- Voeg meer waarden toe aan de wachtrij

myQueue:enqueue(20)

myQueue:enqueue(25)

myQueue:enqueue(30)

-- myQueue = { 10, 15, 20, 25, 30 }

-- Verwijder nog een waarde uit de wachtrij

local second = myQueue:dequeue()

print("De tweede waarde die aan de wachtrij is toegevoegd was", second)

-- myQueue = { 15, 20, 25, 30 }

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
